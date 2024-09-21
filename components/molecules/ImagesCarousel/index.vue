<script lang="ts">
import { computed, defineComponent } from "vue";
export default defineComponent({
  name: "MoleculesImagesCarousel",
  setup() {
    const items = computed(() => {
      return [
        {
          title: "Sistema de login",
          description: "Sistema de login com banco de dados",
          image: "/images/image.png",
          url: "https://github.com/PedroHRFerreira/Sistema-de-Login",
        },
        {
          title: "Sitema-Marketplace",
          description: "Simulação de um Marketplace",
          image: "/images/Captura de tela de 2024-09-21 20-05-13.png",
          url: "https://github.com/PedroHRFerreira/Sitema-Marketplace",
        },
        {
          title: "Projeto",
          description: "Projeto iniciando com Nuxt 3",
          image: "/images/Captura de tela de 2024-09-21 20-10-13.png",
          url: "https://github.com/PedroHRFerreira/Projeto",
        },
        {
          title: "Projeto-bank",
          description: "Simulação de um banco.",
          image: "/images/Captura de tela de 2024-09-21 20-05-13.png",
          url: "https://github.com/PedroHRFerreira/Projeto-do-Bytebank",
        },
      ];
    });

    return {
      items,
    };
  },
});
</script>
<template>
  <section class="carrosel">
    <aside v-for="(item, index) in items" :key="index">
      <article class="carrosel__modal">
        <a :href="item.url" style="text-decoration: none">
          <div class="carrosel__modal--image">
            <img
              :src="item.image"
              :alt="item.title"
              width="100%"
              style="border-radius: 6px"
            />
          </div>
          <div class="carrosel__modal--text">
            <AtomsParagraphTitle
              :text="item.title"
              size="small"
              types="dark-animation"
            />
            <AtomsParagraphTitle
              :text="item.description"
              size="extra-small"
              types="dark-animation"
              class="text"
            />
          </div>
        </a>
      </article>
    </aside>
  </section>
</template>
<style scoped lang="scss">
@import "styles.module.scss";
</style>
