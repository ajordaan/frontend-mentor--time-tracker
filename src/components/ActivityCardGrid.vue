<template>
  <div class="container">
    <activity-card
      class="activity-card"
      v-for="activity in activities"
      :key="activity.title"
      :activity="activity"
      :currentTimeframe="'weekly'"
    ></activity-card>
  </div>
</template>

<script>
import ActivityCard from "./ActivityCard.vue";
export default {
  props: { activities: { type: Array, required: true } },
  components: { ActivityCard },
};
</script>

<style scoped>
.container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  column-gap: 2rem;
}

.activity-card {
  flex-grow: 1;
}
</style>