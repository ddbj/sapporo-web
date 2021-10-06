<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <v-app>
    <script
      id="DDBJ_common_framework"
      defer
      src="https://www.ddbj.nig.ac.jp/assets/js/ddbj_common_framework.js"
      type="text/javascript"
    />
    <v-main class="background">
      <app-bar />
      <v-container fluid>
        <v-card class="mx-auto" max-width="1200">
          <div class="d-flex flex-column mx-6 py-4">
            <div class="d-flex mb-4">
              <v-btn
                color="info"
                outlined
                @click.stop="dumpState"
                v-text="'Dump State'"
              />
              <v-btn
                class="ml-4"
                color="error"
                outlined
                @click.stop="clearState"
                v-text="'Clear State'"
              />
              <v-btn
                class="ml-4"
                color="error"
                outlined
                @click.stop="forceClearState"
              >
                <v-icon left v-text="'mdi-bomb'" />
                <span v-text="'Force Clear State'" />
              </v-btn>
            </div>
            <div
              :style="{
                whiteSpace: 'pre-wrap',
                wordWrap: 'break-word',
              }"
              v-text="stateContent"
            />
          </div>
        </v-card>
      </v-container>
    </v-main>
  </v-app>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import AppBar from '@/components/AppBar.vue'

export default defineComponent({
  components: {
    AppBar,
  },

  computed: {
    stateContent(): string {
      return JSON.stringify(this.$store.state, null, 2)
    },
  },

  methods: {
    dumpState() {
      const blob = new Blob([this.stateContent], { type: 'application/json' })
      const url = window.URL.createObjectURL(blob)
      const link = document.createElement('a')
      link.download = `sapporo-web_state_${this.$dayjs()
        .local()
        .format('YYYY-MM-DD_HH:mm:ss')}.json`
      link.href = url
      link.click()
      link.remove()
      window.URL.revokeObjectURL(url)
    },

    clearState() {
      this.$store.dispatch('services/clearServices')
      this.$store.dispatch('workflows/clearWorkflows')
      this.$store.dispatch('runs/clearRuns')
    },

    forceClearState() {
      this.$store.dispatch('services/clearServices', { force: true })
      this.$store.dispatch('workflows/clearWorkflows', { force: true })
      this.$store.dispatch('runs/clearRuns')
    },
  },
})
</script>
