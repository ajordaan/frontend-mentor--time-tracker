<template>
  <div>
    <div class="card-header rounded-corners" :style="`background-color: ${activity.colour} `">
      <img class="card-image" :src="iconName" />
    </div>
    <div class="card-body rounded-corners">
      <h4 class="card-title">{{ activity.title }}</h4>
      <h3 class="current-hours">{{ activity.timeframes[currentTimeframe].current }}hrs</h3>
      <p>Last Week - {{activity.timeframes[currentTimeframe].previous }}hrs </p>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    activity: { type: Object, required: true },
    currentTimeframe: { type: String, required: true },
  },

  computed: {
    iconName() {
      console.log("BASE URL: " + process.env.BASE_URL);
      console.log("Title: " + this.activity.title.toLowerCase());
      return `${
        process.env.BASE_URL
      }assets/icon-${this.activity.title.toLowerCase().replace(" ", "-")}.svg`;
    },
  },
};
</script>

<style scoped>

.rounded-corners {
  border-radius: 10px;
}
.card-header {
  height: 100px;
  position: relative;
  bottom: -4rem;
  z-index: -1;
  display: flex;
  justify-content: right;
}

.card-image {
  height: 50px;
  padding-right: 0.5rem;
}
.card-body {
  background-color: hsl(235, 46%, 20%);
  padding: 2rem;
  text-align: left;
}

.card-title {
  padding-bottom: 2rem;
}

.current-hours {
  font-size: 3rem;
  padding-bottom: 1rem;
}

.icon-background {
  background-color: hsl(15, 100%, 70%);
}
</style>
