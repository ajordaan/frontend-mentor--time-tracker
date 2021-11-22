<template>
  <div class="container">
    <activity-card
      class="activity-card"
      v-for="activity in activities"
      :key="activity.title"
      :activity="activity"
      :currentTimeframe="currentTime"
      ref="cards"
    ></activity-card>
  </div>
</template>

<script>
import ActivityCard from "./ActivityCard.vue";
export default {
  props: {
    activities: { type: Array, required: true },
    currentTime: { type: String, required: true },
  },
  components: { ActivityCard },
  methods: {
    getTallestCard() {
      let maxHeight = -1;

      for (const card of this.$refs.cards) {
        const cardHeight = card.getCardBodyHeight();
        if (cardHeight > maxHeight) maxHeight = cardHeight;
      }

      return maxHeight;
    },

    setCardBodyHeights(height) {
      for (const card of this.$refs.cards) {
        card.setCardBodyHeight(height);
      }
    },
  },
};
</script>

<style scoped>
.container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  gap: 2rem;
}

.activity-card {
  flex: 1 0 30%;
  margin-top: -4rem;
  /* flex-basis: 25%; */
}
</style>