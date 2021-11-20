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
  mounted() {
    this.resizeCards();
    window.addEventListener("resize", debounce(this.resizeCards, 250));
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

function debounce(func, wait) {
  const timer;
  return function (event) {
    if (timer) clearTimeout(timer);
    timer = setTimeout(func, wait, event);
  };
}
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