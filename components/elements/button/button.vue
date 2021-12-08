<template>
  <button :type="type" class="e-button" :class="classNames" :disabled="disabled">
    <slot />
  </button>
</template>

<script lang="ts">
import Vue from 'vue';

export default Vue.extend({
  props: {
    type: {
      type: String,
      default: 'button',
    },
    disabled: {
      type: Boolean,
      default: false,
    },
  },
  computed: {
    classNames() {
      return {
        disabled: this.disabled,
      };
    },
  },
});
</script>

<style scoped lang="scss">
@use '~assets/css/vars';

.e-button {
  position: relative;
  margin: vars.$size-extra-large auto;
  background-color: transparent;
  color: vars.$black;
  border: 1px solid vars.$black;
  border-radius: 50px;
  padding: vars.$size-small vars.$size-extra-large * 2;
  cursor: pointer;
  font-size: vars.$size-normal;
  z-index: 1;
  &.disabled {
    background-color: vars.$black;
    border: 1px solid vars.$white;
    color: vars.$white;
    cursor: default;
  }
}
</style>
