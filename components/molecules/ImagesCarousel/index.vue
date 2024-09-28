<script lang="ts">
import { computed, defineComponent, ref } from "vue";

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
        {
          title: "Novo Projeto 1",
          description: "Mais um projeto legal.",
          image: "/images/image1.png",
          url: "https://github.com/Example/Project1",
        },
        {
          title: "Novo Projeto 2",
          description: "Outro projeto interessante.",
          image: "/images/image2.png",
          url: "https://github.com/Example/Project2",
        },
      ];
    });

    const currentIndex = ref(0);
    const isLoading = ref(false);

    const startLoading = () => {
      isLoading.value = true;
      setTimeout(() => {
        isLoading.value = false;
      }, 1000);
    };

    const next = () => {
      startLoading();
      if (currentIndex.value < items.value.length - 1) {
        currentIndex.value++;
      } else {
        currentIndex.value = 0;
      }
    };

    const back = () => {
      startLoading();
      if (currentIndex.value > 0) {
        currentIndex.value--;
      } else {
        currentIndex.value = items.value.length - 1;
      }
    };

    const visibleItems = computed(() => {
      return items.value
        .slice(currentIndex.value, currentIndex.value + 4)
        .concat(
          items.value.slice(
            0,
            Math.max(0, currentIndex.value + 4 - items.value.length),
          ),
        );
    });

    return {
      items,
      visibleItems,
      currentIndex,
      isLoading,
      next,
      back,
    };
  },
});
</script>

<template>
  <main class="main" :class="{ loading: isLoading }">
    <section class="carrosel">
      <aside
        v-for="(item, index) in visibleItems"
        :key="index"
        class="anim-loading"
      >
        <article class="carrosel__modal anim-loading">
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
              />
            </div>
          </a>
        </article>
      </aside>
    </section>

    <article class="carrosel-buttons">
      <div class="carrosel-buttons--back" @click="back">
        <AtomsIconSVG name="seta-esquerda" width="32px" height="32px" />
        <AtomsParagraphTitle
          text="Voltar"
          size="small"
          types="dark-animation"
        />
      </div>

      <div class="carrosel-buttons--next" @click="next">
        <AtomsParagraphTitle
          text="Ver mais"
          size="small"
          types="dark-animation"
        />
        <AtomsIconSVG name="mais" width="32px" height="32px" />
      </div>
    </article>
  </main>
</template>
<style scoped lang="scss">
@import "styles.module.scss";
</style>
