<script lang="ts">
import { defineComponent, ref } from "vue";
export default defineComponent({
  name: "MoleculesAnimatedMenu",
  emits: ["onTheme"],
  setup(_, { emit }) {
    const isMenuOpen = ref(false);

    const toggleMenu = () => {
      isMenuOpen.value = !isMenuOpen.value;
    };

    const toggleTheme = () => {
      emit("onTheme");
    };

    return {
      isMenuOpen,
      toggleMenu,
      toggleTheme,
    };
  },
});
</script>
<template>
  <article class="menu-container">
    <div class="hamburger" @click="toggleMenu">
      <div class="bar"></div>
      <div class="bar"></div>
      <div class="bar"></div>
    </div>
    <nav :class="['nav-menu', { open: isMenuOpen }]">
      <ul>
        <li><a href="https://github.com/PedroHRFerreira">GitHub</a></li>
        <li><a href="https://www.instagram.com/pedrohr_dev/">Instagram</a></li>
        <li>
          <a href="https://www.linkedin.com/in/pedro-henrique-2ab9b6302/"
            >LinkedIn</a
          >
        </li>
        <li>
          <AtomsParagraphTitle
            text="Tema💡"
            size="extra-small"
            types="animation"
            @click="toggleTheme"
          />
        </li>
      </ul>
    </nav>
  </article>
</template>
<style scoped lang="scss">
@import "styles.module.scss";
</style>
