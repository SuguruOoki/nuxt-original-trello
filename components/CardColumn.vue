<template>
  <div class="container-card">
    <div><h3>{{ columnTitle }}</h3></div>
    <div v-for="key in sample" :key="key" class="cards">
      <Card :cardContent="key"/>
    </div>
  </div>
</template>
<script>
import Card from './Card.vue'
export default {
  props: {
    columnTitle: {
      type: String,
      require: true
    }
  },
  components: {
    Card
  },
  data() {
    return {
      sample: [1, 2, 3, 4, 5]
    }
  }
}
</script>

<style lang="scss">
$gap-1: 8px;

.container-card {
  background-color: #ebecf0;
  border-radius: 4px;
  min-height: 100px;
  min-width: 80px;
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
}
</style>
