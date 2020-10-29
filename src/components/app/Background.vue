<template>
  <div class="background">
    <div class="wrapper">
      <div v-for="index in count" :key="index" class="element"></div>
    </div>

    <slot></slot>
  </div>
</template>

<script lang="ts">
  import { Component, Prop, Vue } from 'nuxt-property-decorator';

  @Component
  export default class AppBackground extends Vue {
    @Prop(Number) count!: Number;
  }
</script>

<style lang="scss" scoped>
  .background {
    @import '~/assets/styles/color';

    $time: 3.5s;
    $rotate: 55deg;

    @keyframes blurred {
      0% {
        width: 0;
      }

      30% {
        width: 100px;
      }

      100% {
        width: 0;
      }
    }

    @keyframes fall-down {
      0% {
        transform: translateX(0);
      }

      100% {
        transform: translateX(300px);
      }
    }

    width: 100vh;
    height: 100vh;
    overflow: hidden;
    display: flex;
    justify-content: center;
    align-items: center;
    position: absolute;
    top: -20%;

    .wrapper {
      position: relative;
      width: calc(100vw - 50%);
      height: 50%;
      transform: rotateZ($rotate);

      .element {
        position: absolute;
        height: 0.125rem;
        background: linear-gradient(-$rotate, $white-50, $white-0);
        filter: drop-shadow(0 0 0.5rem $white-50);
        animation: blurred $time ease-in-out infinite, fall-down $time ease-in-out infinite;

        &::after {
          @extend .element::before;
          transform: translateX(50%) rotateZ(-$rotate);
        }

        @for $i from 1 through 20 {
          &:nth-child(#{$i}) {
            $delay: random(9999) + 10ms;
            top: calc(50% - #{random(400) - 200px});
            left: calc(50% - #{random(300) + 0px});
            animation-delay: $delay;
            opacity: random(50) / 100 + 0.5;

            &::before,
            &::after {
              animation-delay: $delay;
            }
          }
        }
      }
    }
  }
</style>
