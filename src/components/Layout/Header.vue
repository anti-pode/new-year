<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "AppHeader",
});
</script>

<template>
  <header class="header">
    <img class="desktop" src="@/assets/icons/logo.svg" alt="" />
    <img class="mobile" src="@/assets/icons/logo-mobile.svg" alt="" />
  </header>
</template>

<style lang="scss" scoped>
@import "@/assets/styles/breakpoints";

.header {
  position: relative;
  display: flex;
  align-items: flex-end;
  justify-content: center;
  width: 756px;
  height: 266px;
  margin: 16px auto -21px;
  background: url("@/assets/images/header.png") no-repeat top center / 100%;

  @include --mobile {
    width: 283px;
    height: 128px;
    margin-top: 5px;
    margin-bottom: 18px;
    background-image: url("@/assets/images/header-mobile.png");
  }

  &::before {
    position: absolute;
    top: 16px;
    left: 50%;
    width: 100vw;
    height: 1px;
    background: #000000;
    transform: translateX(-50vw);
    content: "";

    @include --mobile {
      top: 9px;
    }
  }

  .desktop {
    width: 211px;
    margin-bottom: 63px;

    @include --mobile {
      display: none;
    }
  }

  .mobile {
    width: 135px;

    @include --from-mobile {
      display: none;
    }
  }
}
</style>
