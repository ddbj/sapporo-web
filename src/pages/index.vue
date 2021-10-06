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
        <breadcrumbs-header />
        <service-card class="mx-auto mb-4" />
      </v-container>
    </v-main>
  </v-app>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import { MyWindow } from '@/plugins/localStorage'
import AppBar from '@/components/AppBar.vue'
// import AppFooter from '@/components/AppFooter.vue'
import BreadcrumbsHeader from '@/components/BreadcrumbsHeader.vue'
import ServiceCard from '@/components/index/ServiceCard.vue'

export default defineComponent({
  components: {
    AppBar,
    // AppFooter,
    BreadcrumbsHeader,
    ServiceCard,
  },

  middleware({ store }) {
    ;(window as unknown as MyWindow).onNuxtReady(async () => {
      const queue = [store.dispatch('services/updateAllServices')]
      await Promise.all(queue)
    })
  },
})
</script>
