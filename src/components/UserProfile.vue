<template>
  <div class="user-profile-wrapper">
    <div ref="userInfo" class="user-info rounded-corners">
      <img src="@/assets/image-jeremy.png" />
      <h5 class="label">Report for</h5>
      <h2 class="title">Jeremy Robson</h2>
    </div>
    <div ref="timeframe" class="timeframe rounded-corners">
      <ul class="label">
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
  list-style-type: none;
}

.user-info .title {
  font-size: 3rem;
}

.user-info img {
  height: 4rem;
  border: 2px solid #fff;
  border-radius: 50%;
  margin-bottom: 2.5rem;
}

.label {
  color: hsl(236, 100%, 87%);
}

li:hover {
  color: white;
}

.isCurrent {
  color: white;
}

@media screen and (min-width: 1200px) {
  .timeframe ul {
    flex-direction: column;
  }
}
</style>
