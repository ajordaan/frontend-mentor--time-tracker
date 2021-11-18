<template>
  <div class="user-profile-wrapper">
    <div class="user-info rounded-corners">
      <img src="@/assets/image-jeremy.png" />
      <h5>Report for</h5>
      <h2 class="title">Jeremy Robson</h2>
    </div>
    <div class="timeframe rounded-corners">
      <ul>
        <li @click="$emit('timeframeClicked', 'daily')">Daily</li>
        <li @click="$emit('timeframeClicked', 'weekly')">Weekly</li>
        <li @click="$emit('timeframeClicked', 'monthly')">Monthly</li>
      </ul>
    </div>
  </div>
</template>

<script>

export default {};

</script>

<style scoped>
.user-profile-wrapper {
  text-align: left;
}
.user-info {
  background-color: hsl(236, 68%, 71%);
  padding: 2rem 4rem 4rem 2rem;
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
}
li {
  list-style-type: none;
  color: hsl(235, 45%, 61%);
}

li:hover{
  color: white;
}
</style>
