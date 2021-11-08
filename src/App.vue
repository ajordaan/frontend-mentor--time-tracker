<template>
  <div id="app">
    <user-profile></user-profile>
    <activity-card
      v-for="activity in activities"
      :key="activity.title"
      :activity="activity"
      :currentTimeframe="'weekly'"
    ></activity-card>
  </div>
</template>

<script>
import UserProfile from "./components/UserProfile.vue";
import data from "@/assets/data";
import ActivityCard from "./components/ActivityCard.vue";
export default {
  name: "App",
  data() {
    return {
      activities: [],
    };
  },
  created() {
    this.activities = data;
  },
  components: { UserProfile, ActivityCard },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Rubik:wght@300;400;500&display=swap");

body {
  background-color: hsl(226, 43%, 10%);
}
#app {
  font-family: "Rubik", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
