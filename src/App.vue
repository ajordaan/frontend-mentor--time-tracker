<template>
  <div class="wrapper">
    <user-profile
      @timeframeClicked="changed"
      class="user-profile-container"
    ></user-profile>
    <activity-card-grid
      :activities="activities"
      :currentTime="currentTime"
    ></activity-card-grid>
  </div>
</template>

<script>
import UserProfile from "./components/UserProfile.vue";
import data from "@/assets/data";
import ActivityCardGrid from "./components/ActivityCardGrid.vue";
export default {
  name: "App",
  data() {
    return {
      activities: [],
      currentTime: "daily",
    };
  },
  created() {
    this.activities = data;
  },
  components: { UserProfile, ActivityCardGrid },
  methods: {
    changed(time) {
      console.log(time);
      this.currentTime = time;
    },
  },
};
</script>

<style scoped>
.wrapper {
  margin: 5% 10%;
  display: flex;
  align-items: flex-start;
  flex-wrap: wrap;
}
.user-profile-container {
  flex-grow: 1;
}
@media screen and (min-width: 1080px) {
  .wrapper {
    flex-wrap: nowrap;
  }

  .user-profile-container {
    margin-right: 2rem;
  }

.user-profile-container {
  margin-right: 2rem;
}
</style>