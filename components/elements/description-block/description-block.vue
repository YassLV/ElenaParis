<template>
  <div class="description-block">
    <div class="toggle-button" @click="toggleButton" :class="{ active: toggle }" />
    <h2>{{ title }}</h2>
    <p v-if="toggle">{{ description }}</p>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';

interface State {
  toggle: boolean;
}

export default Vue.extend({
  name: 'DescriptionBlock',
  props: {
    title: {
      type: String,
      required: true,
    },
    description: {
      type: String,
      required: true,
    },
  },
  data(): State {
    return {
      toggle: true,
    };
  },
  methods: {
    toggleButton(): void {
      this.toggle = !this.toggle;
    }
  },
});
</script>

<style scoped lang="scss">
@import 'assets/css/vars';

.description-block {
  position: relative;
  background-color: #F6F6F6;
  border: 1px solid #707070;
  min-width: 100px;
  min-height: 30px;
  padding: $size-normal;
  .toggle-button {
    position: absolute;
    cursor: pointer;
    top: 5px;
    right: 5px;
    &:after {
      content: '\25BC';
    }
    &.active {
      &:after {
        content: '\25B2';
      }
    }
  }
  p {
    margin-top: $size-large;
  }
}
</style>
