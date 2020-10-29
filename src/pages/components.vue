<template>
  <main>
    <h1>Components</h1>

    <section>
      <h3>Button</h3>

      <app-button>
        ボタン
      </app-button>
      <br />
      <br />
      <app-button>
        長いボタン 長いボタン 長いボタン 長いボタン
      </app-button>
    </section>

    <section>
      <h3>Background Animation</h3>

      <app-background :count="20"></app-background>
    </section>
  </main>
</template>

<script lang="ts">
  import { Component, Vue } from 'nuxt-property-decorator';

  @Component
  export default class PageComponent extends Vue {
    private head() {
      return { title: 'Components' };
    }
  }
</script>
