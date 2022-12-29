<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "AppHeader",
});
</script>

<template>
  <header class="header">
    <img src="@/assets/icons/logo.svg" alt="" />
  </header>
</template>

<style lang="scss" scoped>
.header {
  position: relative;
  display: flex;
  align-items: flex-end;
  justify-content: center;
  width: 756px;
  height: 266px;
  margin: 16px auto -21px;
  background-image: url("@/assets/images/header.png");

  &::before {
    position: absolute;
    top: 16px;
    left: 50%;
    width: 100vw;
    height: 1px;
    background: #000000;
    transform: translateX(-50vw);
    content: "";
  }

  img {
    margin-bottom: 63px;
  }
}
</style>
