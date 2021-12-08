<template>
  <section class="advantages">
    <div v-for="(grid, key) in $t('grid')" :key="key">
      <img :src="require(`@/assets/images/svg/${grid.icon}.svg`)" :alt="`${grid.icon}-icon`" />
      <p>{{ grid.title }}</p>
      <p>{{ grid.description }}</p>
    </div>
  </section>
</template>

<i18n src="./advantages-section.i18n.yml" lang="yaml" />

<style scoped lang="scss">
@import 'assets/css/vars';

.advantages {
  background-color: $darkBlack;
  padding: $size-extra-large 0;
  text-align: center;
  div p {
    color: $white;
  }
}

@media screen and(min-width: $tablet) {

  .advantages {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-auto-rows: auto;
    grid-gap: $size-extra-large;
    padding: $size-extra-large 20%;
  }
}

</style>
