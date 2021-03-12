<template>
  <div class="container">
    <div
      class="profile"
      v-for="(profile, index) in profiles"
      :key="index"
      :style="{
        'background-image':
          'url(' + require('../assets/' + profile.images[0]) + ')',
      }"
    >
      <div class="overlay">
        <h2>{{ profile.name }}</h2>
        <span> <font-awesome-icon icon="gamepad" /> {{ profile.edition }}</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: () => {
    return {
      //TestDate
      profiles: [
        {
          name: "Call of duty",
          edition: "Activision",
          description: "ffzefezfzefeza",
          images: ["cod1.jpg", "cod2.jpg", "cod3.jpg", "cod4.jpeg"],
          like: false,
          Type: "video Games",
        },

        {
          name: "Battlefield",
          edition: "Electronic Arts",
          description: "ffzefezfzefeza",
          images: ["battlefield.jpeg"],
          like: false,
          Type: "video Games",
        },

        {
          name: "Doom",
          edition: "Bethesda",
          description: "ffzefezfzefeza",
          images: ["doom.jpg"],
          like: false,
          Type: "video Games",
        },

        {
          name: "Halo",
          edition: "Microsoft",
          description: "ffzefezfzefeza",
          images: ["halo.jpeg"],
          like: false,
          Type: "video Games",
        },
      ],
    };
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
  }
}
</style>

