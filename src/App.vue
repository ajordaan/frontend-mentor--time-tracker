<template>
  <div id="app">
    <user-profile></user-profile>
  </div>
</template>

<script>
import UserProfile from "./components/UserProfile.vue";
export default {
  name: "App",
  data() {
    return {
      activities: [],
    };
  },
  created() {
    fetch("src/assets/data.json")
      .then((res) => res.text())
      .then((json) => console.log(json));
  },
  components: { UserProfile },
};
</script>

<style>
body {
  background-color: hsl(226, 43%, 10%);
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
