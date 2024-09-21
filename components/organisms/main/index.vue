<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "OrganismsMain",
  setup() {
    const scrollToAboutSection = () => {
      const element = document.getElementById("organisms-profile");
      if (element) {
        element.scrollIntoView({ behavior: "smooth" });
      }
    };

    return {
      scrollToAboutSection,
    };
  },
});
</script>
<template>
  <div class="main">
    <div class="main__image">
      <img
        src="/public/images/Captura de tela de 2024-08-31 13-13-57.png"
        alt="image"
        class="image"
      />
      <AtomsParagraphTitle
        text="Olá, eu sou Pedro👋"
        size="extra-small"
        types="default"
      />
    </div>
    <div class="main__center">
      <AtomsParagraphTitle
        text="Construindo softwares, landing pages & websites."
        size="large"
        types="animation"
      />
      <AtomsParagraphTitle
        text="Eu, Pedro Henrique, sou apaixonado por programação e estou constantemente em busca de novos desafios para aprimorar minhas habilidades e expandir meu conhecimento. Estou ansioso para enfrentar projetos que estimulem minha criatividade e competência técnica.👇"
        size="medium"
        types="animation"
      />
      <MoleculesButton
        class="button"
        size="small"
        text="Sobre mim"
        type="dark"
        @click="scrollToAboutSection"
      />
    </div>
    <div class="icon">
      <AtomsIconSVG name="seta" />
    </div>
  </div>
</template>
<style scoped lang="scss">
@import "styles.module.scss";
</style>
