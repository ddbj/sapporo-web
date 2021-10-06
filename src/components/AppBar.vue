<template>
  <v-app-bar color="#E99523" dense elevation="4" tag="div">
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
      <v-icon color="white" left v-text="'mdi-book-open-outline'" />
      Docs / FAQ
    </v-btn>
  </v-app-bar>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({})
</script>
