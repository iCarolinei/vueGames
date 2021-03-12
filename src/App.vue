<template>
  <div id="app">
    <ProfileOverview></ProfileOverview>
  </div>
</template>
<script>
import ProfileOverview from "./views/ProfileOverview.vue";

export default {
  name: "App",
  components: {
    ProfileOverview,
  },
};
</script>

<style lang="scss">
body {
  margin: 0;
  padding: 0;
}
@import url("https://fonts.googleapis.com/css2?family=DotGothic16&display=swap");
</style>

