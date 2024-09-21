<script lang="ts">
import { defineComponent, ref } from "vue";
export default defineComponent({
  name: "OrganismsHeader",
  emits: ["toggle"],
  setup(_, { emit }: any) {
    const showModal = ref(false);

    const redirectAbout = () => {
      window.location.href = "https://github.com/PedroHRFerreira";
    };

    const redirect = () => {
      window.location.href = "https://www.instagram.com/pedrohr_dev/";
    };

    const toggleModal = () => {
      emit("toggle");
    };

    return {
      redirect,
      showModal,
      toggleModal,
      redirectAbout,
    };
  },
});
</script>
<template>
  <header class="header">
    <div class="header__email">
      <AtomsIconSVG name="email-svgrepo-com" width="50px" heigth="50px" />
      <AtomsParagraphTitle
        text="devpedrohr@gmail.com"
        size="extra-small"
        types="animation"
      />
    </div>

    <div class="header__about">
      <MoleculesButton
        size="small"
        text="Sobre mim"
        type="dark"
        @click="redirect"
        class="button"
      />
      <MoleculesButton
        size="small"
        text="Contate-me"
        type="dark"
        @click="redirectAbout"
        class="button"
      />
      <img
        class="icon"
        src="/assets/icons/diagram.svg"
        width="50px"
        height="50px"
        alt=""
        @click="toggleModal"
      />
    </div>
  </header>
</template>
<style scoped lang="scss">
@import "styles.module.scss";
</style>
