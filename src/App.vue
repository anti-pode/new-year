<script lang="ts">
import { defineComponent, onMounted, ref } from "vue";

import AppCalendar from "@/components/Calendar/Calendar.vue";
import AppPlayer from "@/components/UI/Player.vue";

// import mockItems from "@/api/items";
import type { IItem } from "@/api/items.types";

export default defineComponent({
  components: { AppCalendar, AppPlayer },
  setup() {
    const items = ref<IItem[] | null>(null);

    onMounted(async () => {
      const _items = await fetch("https://otkazniki.ru/api/advent/", {
        headers: new Headers({
          "Content-Type": "application/json",
        }),
      });

      items.value = await _items.json();
    });

    return {
      items,
    };
  },
});
</script>

<template>
  <div id="#app">
    <section class="container">
      <div class="container__content">
        <h1 class="container__title">Поздравляем вас с новым <span>2023 годом!</span></h1>

        <div class="container__description">
          Тут будет краткий вводный текст про поздравление от&nbsp;Лены и&nbsp;общие слова про новый год.
          И&nbsp;указание что ниже - кнопка для получение подарочка.
        </div>

        <AppPlayer src="/src/assets/media/1.mp4" />
      </div>

      <AppCalendar v-if="items && items.length > 0" :items="items" />
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
