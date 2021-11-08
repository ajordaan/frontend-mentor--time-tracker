<template>
  <div class="wrapper">
    <div class="icon-background">
      <img :src="iconName" />
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
      return "@/assets/icon-" + this.activity.title.toLowerCase() + ".svg";
    },
  },
};
</script>

<style></style>
