<template>
  <div
    class="container"
    :style="{
      'background-image': 'url(' + require('../assets/' + activeImg) + ')',
    }"
  >
    <div class="overlay-gradient">
      <div class="back">
        <font-awesome-icon icon="angle-left" @click="closeProfile" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["profile"],
  data: () => {
    return {
      activeImg: "",
    };
  },
  methods: {
    closeProfile() {
      this.$emit("close");
    },
  },
  beforeMount() {
    this.activeImg = this.profile.images[0];
  },
};
</script>

<style lang="scss" scoped>
.container {
  position: relative;
  width: 100%;
  height: 100%;
  background-position: top center;
  background-size: cover;
}
</style>