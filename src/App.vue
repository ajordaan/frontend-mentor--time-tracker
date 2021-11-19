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

// // Returns a function, that, as long as it continues to be invoked, will not
// // be triggered. The function will be called after it stops being called for
// // N milliseconds. If `immediate` is passed, trigger the function on the
// // leading edge, instead of the trailing.
// function debounce(func, wait, immediate) {
// 	var timeout;
// 	return function() {
// 		var context = this, args = arguments;
// 		var later = function() {
// 			timeout = null;
// 			if (!immediate) func.apply(context, args);
// 		};
// 		var callNow = immediate && !timeout;
// 		clearTimeout(timeout);
// 		timeout = setTimeout(later, wait);
// 		if (callNow) func.apply(context, args);
// 	};
// };
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
}
</style>