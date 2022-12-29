<script lang="ts">
import { defineComponent, onMounted, ref } from "vue";

import AppPlayer from "@/components/UI/Player.vue";
import AppForm from "@/components/UI/Form.vue";

export default defineComponent({
  components: { AppForm, AppPlayer },
});
</script>

<template>
  <div id="#app">
    <section class="container">
      <div class="container__content">
        <h1 class="container__title">Поздравляем вас с&nbsp;новым <span>2023 годом!</span></h1>

        <div class="container__description">
          Тут будет краткий вводный текст про поздравление от&nbsp;Лены и&nbsp;общие слова про новый год.
          И&nbsp;указание что ниже - кнопка для получение подарочка.
        </div>

        <AppPlayer src="/src/assets/media/1.mp4" />

        <AppForm />
      </div>
    </section>
  </div>
</template>

<style lang="scss">
@import "@/assets/styles/breakpoints";
@import "@/assets/styles/fonts";

#app {
  overflow: hidden;
  padding-bottom: 56px;

  @include --tablet {
    padding-bottom: 43px;
  }

  .container {
    &__content {
      max-width: 722px;
    }

    &__title {
      font-family: $font-title;
      font-weight: 700;
      font-size: 72px;
      line-height: 100%;

      span {
        font-family: $font-italic;
        font-weight: 300;
      }
    }

    &__description {
      margin-top: 10px;
      margin-bottom: 37px;
      font-family: $font-title;
      font-weight: 500;
      font-size: 18px;
      line-height: 20px;
    }
  }
}
</style>
