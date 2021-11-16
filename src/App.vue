<template>
  <div class="wrapper">
    <div class="user-profile-container">
      <user-profile></user-profile>
    </div>
    <div class="container">
      <activity-card class="activity-card"
        v-for="activity in activities"
        :key="activity.title"
        :activity="activity"
        :currentTimeframe="'weekly'"
      ></activity-card>
    </div>
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

.container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  gap: 2rem;
.wrapper {
  display: flex;
  /* flex-wrap: wrap; maybe add this in a media query for mobile? */
}

.user-profile-container {
  margin-top: 4rem;
  margin-right: 2rem;
}

.activity-card {
  flex-grow: 1;
}

body {
  background-color: hsl(226, 43%, 10%);
  font-size: 18px;
}
#app {
  font-family: "Rubik", sans-serif;
  font-weight: 300;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #fff;
  margin: 10% 20%;

}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-weight: normal;
}
</style>
