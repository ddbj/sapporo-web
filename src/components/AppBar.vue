<template>
  <v-app-bar color="#E99523" app elevation="8" absolute>
    <v-toolbar-title>
      <nuxt-link class="white--text text-decoration-none" to="/">
        DDBJ Workflow Execution Service
      </nuxt-link>
    </v-toolbar-title>
    <v-spacer />
    <v-btn
      class="text-capitalize"
      color="white"
      href="https://hackmd.io/@suecharo/sapporo-web-docs"
      outlined
    >
      <v-icon left color="white" v-text="'mdi-book-open-outline'" />
      Docs
    </v-btn>
  </v-app-bar>
</template>

<script lang="ts">
import { ThisTypedComponentOptionsWithRecordProps } from 'vue/types/options'
import Vue from 'vue'

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
> = {}

export default Vue.extend(options)
</script>
