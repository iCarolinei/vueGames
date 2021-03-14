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
    <transition name="fade">
      <ProfilePage
        v-if="active"
        :profile="activeProfile"
        @close="closeProfile"
      />
    </transition>
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
          description:
            "Call of Duty is a first-person shooter video game franchise published by Activision. Starting out in 2003, it first focused on games set in World War II. Over time, the series has seen games set in the midst of the Cold War, futuristic worlds, and outer space.",
          images: ["cod1.jpg", "cod2.jpg", "cod3.jpg", "cod4.jpeg"],
          like: false,
          style: "fps1",
        },

        {
          name: "Battlefield",
          edition: "Electronic Arts",
          description:
            "Battlefield is a series of first-person shooter video games that started out on Microsoft Windows and OS X with Battlefield 1942, which was released in 2002. The series is developed by Swedish company EA DICE and is published by American company Electronic Arts.",
          images: ["battlefield.jpeg"],
          like: false,
          style: "fps2",
        },

        {
          name: "Doom",
          edition: "Bethesda",
          description:
            "Doom is considered one of the pioneering first-person shooter games, introducing to IBM-compatible computers features such as 3D graphics, third-dimension spatiality, networked multiplayer gameplay, and support for player-created modifications with the Doom WAD format. ",
          images: ["doom.jpg"],
          like: false,
          style: "fps3",
        },

        {
          name: "Halo",
          edition: "Microsoft",
          description:
            "Halo is an American military science fiction media franchise managed and developed by 343 Industries and published by Xbox Game Studios. The franchise and its early main installments were originally developed by Bungie. The central focus of the franchise builds off the experiences of Master Chief John-117.",
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
      font-size: 1.5rem;
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
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s linear;
}
.fade-enter,
.fade-leave-to {
  opacity: 0;
}
</style>

