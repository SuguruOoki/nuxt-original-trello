<template>
  <div class="card">{{ cardContent }}</div>
</template>

<script>
export default {
  props: {
    cardContent: {
      type: Number,
      require: true,
      default: ''
    }
  }
}
</script>

<style lang="scss" scoped>
.card {
  background-color: #ffffff;
  color: #172b4d;
  border-radius: 4px;
  padding: 12px 16px;
  min-height: 16px;
}
</style>
