<template>
  <div class="card">
    <div class="icon-background">
      <img :src="iconName" />
    </div>
    <div class="card-body">
      <h4>{{ activity.title }}</h4>
      <h3>{{ activity.timeframes[currentTimeframe].current }}hrs</h3>
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
.card-body {
  background-color: hsl(235, 46%, 20%);
}

.icon-background {
  background-color: hsl(15, 100%, 70%);
}
</style>
