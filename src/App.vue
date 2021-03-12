<template>
  <div>
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
</style>

