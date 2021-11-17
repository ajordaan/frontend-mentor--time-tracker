<template>
  <div class="container">
    <activity-card
      class="activity-card"
      v-for="activity in activities"
      :key="activity.title"
      :activity="activity"
      :currentTimeframe="currentTime"
    ></activity-card>
  </div>
</template>

<script>
import ActivityCard from "./ActivityCard.vue";
export default {
  props: { 
    activities: { type: Array, required: true }
  ,currentTime: {type: String, required: true} },
  components: { ActivityCard },
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
  flex: 1 25%;
  margin-top: -4rem;
/* flex-basis: 25%; */
}
</style>