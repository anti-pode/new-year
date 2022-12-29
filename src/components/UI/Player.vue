<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "AppPlayer",
  props: {
    src: {
      type: String,
      required: true,
    },
  },
  setup() {},
});
</script>

<template>
  <div class="video">
    <video :src="src" controls autoplay loop></video>
  </div>
</template>

<style lang="scss" scoped>
@import "@/assets/styles/breakpoints";

.video {
  width: 100%;

  @include --mobile {
    width: calc(100% + 48px);
    margin-left: -24px;
  }

  video {
    display: block;
    width: 100%;
  }
}
</style>
