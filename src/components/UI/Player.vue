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
.video {
  width: 100%;

  video {
    width: 100%;
  }
}
</style>
