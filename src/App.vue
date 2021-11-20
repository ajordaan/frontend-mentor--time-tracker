<template>
  <div class="wrapper">
    <user-profile
      @timeframeClicked="changed"
      class="user-profile-container"
      ref="userProfile"
    ></user-profile>
    <activity-card-grid
      :activities="activities"
      :currentTime="currentTime"
      ref="activityCards"
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
    resizeCards() {
      const cardHeight = this.$refs.activityCards.getTallestCard();
      this.$refs.activityCards.setCardBodyHeights(cardHeight);
      const cardGridHeight = this.$refs.activityCards.$el.clientHeight;
      const userProfileHeight = this.$refs.userProfile.$el.clientHeight;
      const heightDifference = cardGridHeight - userProfileHeight;

      this.$refs.userProfile.$refs.userInfo.style.height =
        this.$refs.userProfile.$refs.userInfo.clientHeight +
        heightDifference +
        convertRemToPixels(2) +
        "px";
    },
  },
};

function convertRemToPixels(rem) {
  return rem * parseFloat(getComputedStyle(document.documentElement).fontSize);
}
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