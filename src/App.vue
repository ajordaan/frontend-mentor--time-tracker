<template>
  <div class="wrapper">
    <user-profile class="user-profile-container"></user-profile>
    <activity-card-grid :activities="activities" class="activity-card-grid-container"></activity-card-grid>
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
    };
  },
  created() {
    this.activities = data;
  },
  components: { UserProfile, ActivityCardGrid },
};
</script>

<style scoped>
.wrapper {
  display: flex;
  /* flex-wrap: wrap; maybe add this in a media query for mobile? */
}

.user-profile-container {
  margin-top: 4rem;
  margin-right: 2rem;
  width: 30%;
}
.activity-card-grid-container{
  width: 70%;
}

</style>
