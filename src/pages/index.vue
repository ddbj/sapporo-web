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
        <breadcrumbs />
        <service-card class="mx-auto mb-4" />
      </v-container>
    </v-main>
  </v-app>
</template>

<script lang="ts">
import { ThisTypedComponentOptionsWithRecordProps } from 'vue/types/options'
import Vue from 'vue'
import { MyWindow } from '@/plugins/localStorage'
import AppBar from '@/components/AppBar.vue'
import Breadcrumbs from '@/components/Breadcrumbs.vue'
import ServiceCard from '@/components/index/ServiceCard.vue'

type Data = Record<string, unknown>

type Methods = Record<string, unknown>

type Computed = Record<string, unknown>

type Props = Record<string, unknown>

const options: ThisTypedComponentOptionsWithRecordProps<
  Vue,
  Data,
  Methods,
  Computed,
  Props
> = {
  components: {
    AppBar,
    Breadcrumbs,
    ServiceCard,
  },

  middleware({ store }) {
    ;(window as unknown as MyWindow).onNuxtReady(async () => {
      const queue = [store.dispatch('services/updateAllServices')]
      await Promise.all(queue)
    })
  },
}

export default Vue.extend(options)
</script>
