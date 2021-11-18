<template>
  <div class="user-profile-wrapper">
    <div class="user-info rounded-corners">
      <img src="@/assets/image-jeremy.png" />
      <h5>Report for</h5>
      <h2 class="title">Jeremy Robson</h2>
    </div>
    <div class="timeframe rounded-corners">
      <ul>
        <li @click="$emit('timeframeClicked', 'daily'); addClass('daily');" :class="{isCurrent: isDailyActive}" >Daily</li>
        <li @click="$emit('timeframeClicked', 'weekly'); addClass('weekly')" :class="{isCurrent: isWeeklyActive}">Weekly</li>
        <li @click="$emit('timeframeClicked', 'monthly'); addClass('monthly')" :class="{isCurrent: isMonthlyActive}">Monthly</li>
      </ul>
    </div>
  </div>
</template>

<script>

export default {
  data(){
    return{
      isDailyActive: false,
      isWeeklyActive: false,
      isMonthlyActive: false
    }
  },
  methods:{
    addClass(clicked){
      this.isDailyActive = false
      this.isWeeklyActive = false
      this.isMonthlyActive = false
      if(clicked == 'daily'){
        this.isDailyActive = true
      }
      if(clicked == 'weekly'){
        this.isWeeklyActive = true
      }
      if(clicked == 'monthly'){
        this.isMonthlyActive = true
      }
      
      console.log(clicked)
  }
  }
}

</script>

<style scoped>
.user-profile-wrapper {
  text-align: left;
}
.user-info {
  background-color:hsl(246, 80%, 60%);
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

li:active{
  color: white;
}

.isCurrent{
  color:white;
}

</style>
