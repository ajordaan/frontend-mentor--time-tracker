<template>
  <div>
    <div
      class="card-header rounded-corners"
      :style="`background-color: ${activity.colour} `"
    >
      <img class="card-image" :src="iconName" />
    </div>
    <div ref="cardBody" class="card-body rounded-corners">
      <h4 class="card-title">
        {{ activity.title }} <img src="/assets/icon-ellipsis.svg" alt="" />
      </h4>
      <div class="hours">
        <h3 class="current-hours">
          {{ activity.timeframes[currentTimeframe].current }}hrs
        </h3>
        <p>
          {{ timeframeString }} -
          {{ activity.timeframes[currentTimeframe].previous }}hrs
        </p>
      </div>
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
      return `${process.env.BASE_URL}assets/icon-${this.activity.title
        .toLowerCase()
        .replace(" ", "-")}.svg`;
    },
    timeframeString() {
      switch (this.currentTimeframe) {
        case "daily":
          return "Yesterday";
        case "weekly":
          return "Last week";
        case "monthly":
          return "Last month";
      }
      return "";
    },
  },

  methods: {
    getCardBodyHeight() {
      return this.$refs.cardBody.clientHeight;
    },
    setCardBodyHeight(height) {
      this.$refs.cardBody.style.height = height + "px";
    },
  },
};
</script>

<style scoped>
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
  /* Offset the card header bottom position */
  /* margin-bottom: -4rem;  */
}

.card-body:hover {
  background-color: hsl(235, 45%, 61%);
}

.card-title {
  padding-bottom: 0.5rem;
}

.card-title img {
  float: right;
  margin-top: 0.4rem;
}

.current-hours {
  font-size: 2.5rem;
}

.hours {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

p {
  color: hsl(236, 100%, 87%);
}

.icon-background {
  background-color: hsl(15, 100%, 70%);
}

@media screen and (min-width: 1200px) {
  .hours {
    justify-content: flex-start;
    align-items: center;
    flex-direction: column;
  }

  .current-hours {
    padding-bottom: 1rem;
  }

  .card-title {
  padding-bottom: 2rem;
}
}
</style>
