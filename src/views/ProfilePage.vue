<template>
  <div
    class="container"
    :style="{
      'background-image': 'url(' + require('../assets/' + activeImg) + ')',
    }"
  >
    <div :class="'overlay-gradient ' + profile.style">
      <div class="back">
        <font-awesome-icon icon="angle-left" @click="closeProfile" />
      </div>
      <div class="actions">
        <font-awesome-icon
          :icon="['far', 'heart']"
          v-if="!profile.like"
          @click="profile.like = !profile.like"
        />
        <font-awesome-icon
          :icon="['fas', 'heart']"
          class="red"
          v-if="profile.like"
          @click="profile.like = !profile.like"
        />
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
  transition: all 0.4s linear;
  .overlay-gradient {
    width: 100%;
    height: calc(100% - 20px);
    padding-top: 20px;
  }
  .fps1 {
    background: linear-gradient(
      to bottom,
      rgba($color: #fff, $alpha: 0) 30%,
      rgba($color: #845ec2, $alpha: 1) 80%,
      rgba($color: #845ec2, $alpha: 1) 100%
    );
  }
  .fps2 {
    background: linear-gradient(
      to bottom,
      rgba($color: #fff, $alpha: 0) 30%,
      rgba($color: #d65db1, $alpha: 1) 80%,
      rgba($color: #d65db1, $alpha: 1) 100%
    );
  }
  .fps3 {
    background: linear-gradient(
      to bottom,
      rgba($color: #fff, $alpha: 0) 30%,
      rgba($color: #ff6f91, $alpha: 1) 80%,
      rgba($color: #ff6f91, $alpha: 1) 100%
    );
  }
  .fps4 {
    background: linear-gradient(
      to bottom,
      rgba($color: #fff, $alpha: 0) 30%,
      rgba($color: #ff9671, $alpha: 1) 80%,
      rgba($color: #ff9671, $alpha: 1) 100%
    );
  }
  .back {
    position: absolute;
    top: 0;
    left: 0;
    padding: 20px;

    .fa-angle-left {
      font-size: 4rem;
      cursor: pointer;
      color: white;
    }
  }
  .actions {
    position: absolute;
    top: 0;
    right: 0;
    padding: 25px 20px;

    .red {
      color: red;
    }

    .fa-heart {
      font-size: 3rem;
      cursor: pointer;
      color: white;
    }
  }
}
</style>