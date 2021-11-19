<template>
  <div class="user-profile-wrapper">
    <div class="user-info rounded-corners">
      <img src="@/assets/image-jeremy.png" />
      <h5>Report for</h5>
      <h2 class="title">Jeremy Robson</h2>
    </div>
    <div class="timeframe rounded-corners">
      <ul>
        <li
          @click="timeframeClicked('daily')"
          :class="{ isCurrent: selectedTime == 'daily' }"
        >
          Daily
        </li>
        <li
          @click="timeframeClicked('weekly')"
          :class="{ isCurrent: selectedTime == 'weekly' }"
        >
          Weekly
        </li>
        <li
          @click="timeframeClicked('monthly')"
          :class="{ isCurrent: selectedTime == 'monthly' }"
        >
          Monthly
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      selectedTime: "daily",
    };
  },
  methods: {
    timeframeClicked(time) {
      this.selectedTime = time;
      this.$emit("timeframeClicked", time);
    },
  },
};
</script>

<style scoped>
.user-profile-wrapper {
  text-align: left;
}
.user-info {
  background-color: hsl(246, 80%, 60%);
  padding: 2rem 4rem 4rem 2rem;
  position: relative;
  z-index: 2;
}

.timeframe {
  background-color: hsl(235, 46%, 20%);
  padding: 4rem 4rem 2rem 2rem;
  position: relative;
  top: -2rem;
}

.timeframe li {
  padding-bottom: 1rem;
}

.user-info .title {
  font-size: 3rem;
}

.user-info img {
  height: 4rem;
  padding: 1px;
  border: 2px solid #fff;
  border-radius: 50%;
}
li {
  list-style-type: none;
  color: hsl(235, 45%, 61%);
}

li:hover {
  color: white;
}

li:active {
  color: white;
}

.isCurrent {
  color: white;
}
</style>
