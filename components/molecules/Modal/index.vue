<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "MoleculesModal",
  props: {
    showModal: {
      type: Boolean,
      required: true,
      default: false,
    },
  },
  emits: ["toggleModal"],
  setup(props, { emit }) {
    const toggleModal = () => {
      emit("toggleModal");
    };

    return {
      toggleModal,
    };
  },
});
</script>
<template>
  <img
    class="icon"
    src="/assets/icons/diagram.svg"
    width="50px"
    height="50px"
    alt=""
    @click="toggleModal"
  />
  <aside v-if="showModal" class="modal">
    <article class="modal__main">
      <section class="modal__main--header">
        <AtomsParagraphTitle
          text="Olá nesse novo mundo👋"
          size="small"
          types="dark-animation"
          class="text"
        />
        <article class="section-icon">
          <AtomsIconSVG name="github-fill-svgrepo-com" />
          <AtomsIconSVG name="instagram" />
          <AtomsIconSVG name="close" @click="toggleModal" />
        </article>
      </section>
    </article>
    <article class="modal__center">
      <slot />
    </article>
  </aside>
</template>
<style scoped lang="scss">
@import "styles.module.scss";
</style>
