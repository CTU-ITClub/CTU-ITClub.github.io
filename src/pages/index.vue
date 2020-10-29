<template>
  <main></main>
</template>

<script lang="ts">
  import { Component, Vue } from 'nuxt-property-decorator';

  @Component
  export default class PageIndex extends Vue {
    private head() {
      return { title: 'Home' };
    }
  }
</script>
