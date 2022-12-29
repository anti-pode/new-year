<script lang="ts">
import { defineComponent, ref } from "vue";
import AppButton from "@/components/UI/Button.vue";
import AppBaseModal from "@/components/Modals/BaseModal.vue";
import AppPromoModal from "@/components/Modals/PromoModal.vue";

const MOCK_POPUP_DATA = {
  id: 1,
  title: "Вам подарок от ЛитРес!",
  gift: "Друг фонда – книжный сервис ЛитРес дарит вам книгу из подборки и скидку 20% на каталог!",
  code: "ADVENT20",
  link: "https://www.google.ru/",
  description:
    "Скидка действует в течение 3-х дней с момента активации на одну покупку и неограниченное количество книг в корзине. Скидка не суммируется с другими акциями и спецпредложениями. Скидка не распространяется на ЛитРес: Абонемент и ЛитРес: Подписка.",
};

export default defineComponent({
  name: "AppForm",
  components: { AppPromoModal, AppBaseModal, AppButton },
  setup() {
    const isModalVisible = ref<boolean>(false);

    const submit = () => {
      console.log(123);
      isModalVisible.value = true;
    };

    const onPopupClose = () => {
      isModalVisible.value = false;
    };

    return {
      submit,
      onPopupClose,
      isModalVisible,
      MOCK_POPUP_DATA,
    };
  },
});
</script>

<template>
  <form class="form" @submit.prevent="submit">
    <div class="input">
      <input type="email" id="email" placeholder=" " required />
      <label for="email">Ваша электронная почта</label>
    </div>

    <AppButton text="Получить подарок" is-submit />

    <teleport to="body">
      <AppBaseModal v-if="isModalVisible" @close="onPopupClose">
        <AppPromoModal v-bind="MOCK_POPUP_DATA" />
      </AppBaseModal>
    </teleport>
  </form>
</template>

<style lang="scss" scoped>
@import "@/assets/styles/breakpoints";

.form {
  display: flex;
  margin-top: 39px;

  @include --tablet {
    margin-bottom: 90px;
  }

  @include --mobile {
    flex-direction: column;
    margin-top: 34px;
    margin-bottom: 60px;
  }

  .input {
    position: relative;
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    width: 393px;
    height: 56px;
    margin-right: 14px;
    padding: 10px 16px;
    background-color: #fff;
    border: 1px solid #c0c4cb;
    border-radius: 3px;

    @include --mobile {
      width: 100%;
      margin: 0 0 25px 0;
    }

    input {
      width: 100%;
      padding: 0;
      background: transparent;
      border: 0;

      &:not(:placeholder-shown) + label,
      &:focus + label {
        top: 8px;
        font-size: 12px;
      }
    }

    label {
      position: absolute;
      top: 20px;
      left: 16px;
      font-weight: 400;
      font-size: 18px;
      line-height: 1;
      color: #a1a5ae;
      transition: all 0.3s ease;
    }
  }

  .btn {
    @include --from-mobile {
      padding-top: 0;
      padding-bottom: 0;
    }

    @include --mobile {
      height: 56px;
    }
  }
}
</style>
