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
    ></div>
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
          style: "Fps",
          description: "ffzefezfzefeza",
          images: ["cod1.jpeg", "cod2.jpg", "cod3.jpg", "cod4.jpeg"],
          like: false,
          Type: "video Games",
        },

        {
          name: "Battlefield",
          style: "Fps",
          description: "ffzefezfzefeza",
          images: ["battlefield.jpeg"],
          like: false,
          Type: "video Games",
        },

        {
          name: "Doom",
          style: "Fps",
          description: "ffzefezfzefeza",
          images: ["doom.jpg"],
          like: false,
          Type: "video Games",
        },

        {
          name: "Halo",
          style: "Fps",
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
  }
}
</style>

