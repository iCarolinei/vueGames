<template>
  <div class="container">
    <div
      class="profile"
      v-for="(profile, index) in profiles"
      :key="index"
      @click="setProfile(index)"
      :style="{
        'background-image':
          'url(' + require('../assets/' + profile.images[0]) + ')',
      }"
    >
      <div :class="'overlay ' + profile.style">
        <h2>{{ profile.name }}</h2>
        <span> <font-awesome-icon icon="gamepad" /> {{ profile.edition }}</span>
      </div>
    </div>
    <ProfilePage v-if="active" :profile="activeProfile" @close="closeProfile" />
  </div>
</template>

<script>
import ProfilePage from "./ProfilePage.vue";

export default {
  data: () => {
    return {
      active: false,
      activeProfile: {},
      profiles: [
        {
          name: "Call of duty",
          edition: "Activision",
          description: "ffzefezfzefeza",
          images: ["cod1.jpg", "cod2.jpg", "cod3.jpg", "cod4.jpeg"],
          like: false,
          style: "fps1",
        },

        {
          name: "Battlefield",
          edition: "Electronic Arts",
          description: "ffzefezfzefeza",
          images: ["battlefield.jpeg"],
          like: false,
          style: "fps2",
        },

        {
          name: "Doom",
          edition: "Bethesda",
          description: "ffzefezfzefeza",
          images: ["doom.jpg"],
          like: false,
          style: "fps3",
        },

        {
          name: "Halo",
          edition: "Microsoft",
          description: "ffzefezfzefeza",
          images: ["halo.jpeg"],
          like: false,
          style: "fps4",
        },
      ],
    };
  },
  methods: {
    setProfile(index) {
      this.activeProfile = this.profiles[index];
      this.active = true;
    },
    closeProfile() {
      this.active = false;
    },
  },

  components: {
    ProfilePage,
  },
};
</script>

<style lang="scss" scoped>
.container {
  position: relative;
  width: 100%;
  height: 100vh;

  .profile {
    position: relative;
    float: left;
    width: 50%;
    height: 50%;
    background-position: top center;
    background-size: cover;
    cursor: pointer;
  }
  .overlay {
    position: absolute;
    bottom: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    width: 100%;
    height: 20%;
    padding-top: 40px;
    font-family: "DotGothic16", sans-serif;
    background: linear-gradient(
      to bottom,
      rgba($color: #fff, $alpha: 0) 0%,
      rgba($color: #fff, $alpha: 1) 100%
    );

    h2 {
      font-size: 2rem;
      padding: 0;
      margin: 0;
    }

    span {
      font-size: 1rem;
      font-weight: bold;
    }
  }

  .fps1 {
    color: #845ec2;
  }
  .fps2 {
    color: #d65db1;
  }
  .fps3 {
    color: #ff6f91;
  }
  .fps4 {
    color: #ff9671;
  }
}
</style>

