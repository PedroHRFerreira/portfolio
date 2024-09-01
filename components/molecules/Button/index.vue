<script lang="ts">
import { defineComponent } from "vue";
export default defineComponent({
  name: "moleculesButton",
  props: {
    size: {
      type: String,
      default: "primary",
      validator: (value: string) => {
        return ["small", "primary", "medium", "big"].includes(value);
      },
    },
    type: {
      type: String,
      default: "default",
      validator: (value: string) => {
        return ["default", "cancel", "dark"].includes(value);
      },
    },
    sizeText: {
      type: String,
      default: "extra-small",
    },
    text: {
      type: String,
      default: "Button test",
    },
    typesText: {
      type: String,
      default: "default",
    },
  },
  emits: ["Onclick"],
  setup(props, { emit }) {
    const ButtonClick = () => {
      emit("Onclick");
    };
    return {
      ButtonClick,
    };
  },
});
</script>
<template>
  <button
    class="recreational-button"
    :class="[size, type]"
    @click="ButtonClick"
  >
    <AtomsParagraphTitle :size="sizeText" :text="text" :types="typesText" />
  </button>
</template>
<style scoped lang="scss">
@import "styles.module.scss";
</style>
