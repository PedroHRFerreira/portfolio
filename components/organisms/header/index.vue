<script lang="ts">
import { defineComponent } from "vue";
export default defineComponent({
  name: "OrganismsHeader",
  setup() {
    const redirectAbout = () => {
      window.location.href = "https://github.com/PedroHRFerreira";
    };

    const redirect = () => {
      window.location.href = "https://www.instagram.com/pedrohr_dev/";
    };

    return {
      redirectAbout,
      redirect,
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
      />
      <MoleculesButton
        size="small"
        text="Contate-me"
        type="dark"
        @click="redirectAbout"
      />
    </div>
  </header>
</template>
<style scoped lang="scss">
@import "styles.module.scss";
</style>
