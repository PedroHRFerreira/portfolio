<script lang="ts">
import { defineComponent, ref } from "vue";

export default defineComponent({
  name: "LayoutDefault",
  setup() {
    const showModal = ref(true);

    const handleToggleModal = () => {
      showModal.value = !showModal.value;
    };

    return {
      showModal,
      handleToggleModal,
    };
  },
});
</script>

<template>
  <div class="layout-container">
    <video autoplay muted loop class="background-video">
      <source
        src="/public/images/1449850-hd_1906_1080_28fps.mp4"
        type="video/mp4"
      />
      Seu navegador não suporta o elemento de vídeo.
    </video>

    <video v-if="showModal" autoplay muted loop class="background-video">
      <source
        src="/public/images/854569-hd_1920_1080_25fps.mp4"
        type="video/mp4"
      />
      Seu navegador não suporta o elemento de vídeo.
    </video>

    <header class="layout-header">
      <OrganismsHeader @toggle="handleToggleModal" />
    </header>
    <main class="layout-main">
      <section class="layout-content">
        <OrganismsMain />
        <MoleculesImagesCarousel />
        <OrganismsProfile id="organisms-profile" />
      </section>
    </main>
  </div>
</template>

<style scoped lang="scss">
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

html,
body {
  height: 100%;
  width: 100%;
}

.layout-container {
  display: flex;
  flex-direction: column;
  min-height: 100vh;

  .background-video {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    object-fit: cover;
    z-index: -1;
    animation: fadeIn 3s ease-in-out;
  }

  @keyframes fadeIn {
    from {
      opacity: 0;
    }
    to {
      opacity: 1;
    }
  }

  .layout-header {
    z-index: 1;
  }

  .layout-main {
    flex: 1;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;

    #organisms-profile {
      z-index: 1;
    }
  }
}
</style>
