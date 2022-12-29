<script lang="ts">
import { defineComponent } from "vue";

import AppPlayer from "@/components/UI/Player.vue";
import AppForm from "@/components/UI/Form.vue";
import AppHeader from "@/components/Layout/Header.vue";

export default defineComponent({
  components: { AppHeader, AppForm, AppPlayer },
});
</script>

<template>
  <div id="#app">
    <section class="container">
      <AppHeader />

      <div class="main-content">
        <div class="main-content__container">
          <h1 class="main-content__title">Поздравляем вас с&nbsp;новым <span>2023 годом!</span></h1>

          <div class="main-content__description">
            Тут будет краткий вводный текст про поздравление от&nbsp;Лены и&nbsp;общие слова про новый год.
            И&nbsp;указание что ниже - кнопка для получение подарочка.
          </div>

          <AppPlayer src="/src/assets/media/1.mp4" />

          <AppForm />
        </div>

        <div class="main-content__aside">
          <img src="@/assets/images/tree.png" alt="" />
        </div>
      </div>
    </section>

    <div class="santa">
      <img src="@/assets/images/santa.png" alt="" />
    </div>
  </div>
</template>

<style lang="scss">
@import "@/assets/styles/breakpoints";
@import "@/assets/styles/fonts";

#app {
  position: relative;
  overflow: hidden;

  &::after {
    position: absolute;
    top: 65px;
    left: 50%;
    width: 1388px;
    height: 1031px;
    background: url("@/assets/images/stars.png") no-repeat top center / 100%;
    transform: translateX(-50%);
    pointer-events: none;
    content: "";
  }

  .main-content {
    display: flex;

    &__container {
      flex-shrink: 0;
      max-width: 722px;
    }

    &__aside {
      flex-shrink: 0;
      width: 493px;
      height: 903px;
      margin-left: -15px;

      img {
        display: block;
        width: 100%;
        height: 100%;
      }
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

  .santa {
    position: absolute;
    bottom: 0;
    left: 0;

    img {
      display: block;
    }
  }
}
</style>
