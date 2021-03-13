<template>
  <div
    class="container"
    :style="{
      'background-image': 'url(' + require('../assets/' + activeImg) + ')',
    }"
  ></div>
</template>

<script>
export default {
  props: ["profile"],
  data: () => {
    return {
      activeImg: "",
    };
  },
  beforeMount() {
    this.activeImg = this.profile.images[0];
  },
};
</script>

<style lang="scss" scoped>
</style>