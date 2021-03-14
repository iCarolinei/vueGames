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
      <div class="overlay">
        <h1 class="overlay-name">{{ profile.name }}</h1>
        <span class="overlay-style"
          ><font-awesome-icon icon="gamepad" /> {{ profile.edition }}</span
        >
        <p>{{ profile.description }}</p>
        <div class="gallery">
          <div
            class="gallery-img"
            :class="{ inactiv: activeImg !== image }"
            v-for="(image, index) in profile.images"
            :key="index"
          >
            <span class="img-container">
              <img
                :src="require('../assets/' + image)"
                @click="activeImg = image"
                alt=""
              />
            </span>
          </div>
        </div>
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
      color: red !important;
    }

    .fa-heart {
      font-size: 3rem;
      cursor: pointer;
      color: white;
      transition: color 0.4s linear;

      &:hover {
        color: red;
      }
    }
  }
  .overlay {
    position: absolute;
    bottom: 0;
    width: calc(100% - 40px);
    padding: 100px 20px 10px;
    font-family: "DotGothic16", sans-serif;
    color: white;
    text-align: center;
    h1 {
      font-size: 4.8rem;
      line-height: 4.8rem;
      font-weight: bold;
      margin: 0;
      padding: 0;
    }
    .overlay-name {
      margin-bottom: 20px !important;
    }
    .overlay-style {
      font-size: 20px;
      font-weight: 600;
    }
    p {
      font-style: italic;
      width: 100%;
    }
    .gallery {
      display: flex;
      justify-content: space-between;
      align-items: center;
      width: 100%;
      height: 100px;

      .gallery-img {
        width: 80px;
        height: 80px;
        border-radius: 50%;
        overflow: hidden;
        cursor: pointer;
        box-shadow: 0 15px 30px rgba(0, 0, 0, 0.2),
          0 10px 10px rgba(0, 0, 0, 0.2);
        transition: transform 0.2s linear;
        .img-container {
          text-align: center;
          display: block;
        }
        img {
          max-width: 80px;
          height: 80px;
          object-fit: cover;
        }
      }
      .inactiv {
        opacity: 0.7;
        box-shadow: none;
        transition: transform 0.2s linear;
        &:hover {
          opacity: 1;
          transform: scale(1.1);
          box-shadow: 0 15px 30px rgba(0, 0, 0, 0.2),
            0 10px 10px rgba(0, 0, 0, 0.2);
        }
      }
    }
  }
}
</style>