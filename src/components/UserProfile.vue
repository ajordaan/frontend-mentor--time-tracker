<template>
  <div class="user-profile-wrapper">
    <div ref="userInfo" class="user-info rounded-corners">
      <img src="@/assets/image-jeremy.png" />
      <div class="userTitleAndLabel">
        <h5 class="label">Report for</h5>
        <h2 class="title">Jeremy Robson</h2>
      </div>
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
  padding: 1rem;
  position: relative;
  z-index: 2;
  display: flex;
  align-items: center;
}

.timeframe {
  background-color: hsl(235, 46%, 20%);
  padding: 4rem 2rem 2rem 2rem;
  position: relative;
  top: -2rem;
}

.timeframe ul {
  display: flex;
  justify-content: space-between;
}

.timeframe li {
  list-style-type: none;
}

.user-info .title {
  font-size: 1.5rem;
}

.user-info img {
  height: 5rem;
  border: 2px solid #fff;
  border-radius: 50%;
  margin-right: 1rem;
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
  .user-info .title {
    font-size: 3rem;
  }

  .user-info img {
    margin-bottom: 2rem;
  }

  .user-info {
    padding: 2rem 4rem 4rem 2rem;
    display: block;
  }

  .timeframe {
    padding: 4rem 4rem 2rem 2rem;
  }

  .timeframe li {
    padding-bottom: 1rem;
  }
}
</style>
