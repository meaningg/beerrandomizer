<template>
  <div class="container">
    <profile-card />
    <beer-card />
  </div>
</template>

<script>
import BeerCard from "./components/BeerCard.vue";
import ProfileCard from "./components/ProfileCard.vue";
export default {
  components: { ProfileCard, BeerCard },
};
</script>

<style lang="scss">
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
    Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
}
.container {
  width: 100%;
  min-height: 100%;
  position: absolute;
  background-color: rgb(20, 20, 20);
  display: flex;
  gap: 10px;
  justify-content: center;
  flex-wrap: wrap;
  padding: 5%;
}
</style>
