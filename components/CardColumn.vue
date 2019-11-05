<template>
  <div class="container-card">
    <div v-for="key in sample" :key="key" class="cards">
      <Card/>
    </div>
  </div>
</template>
<script>
import Card from './Card.vue'
export default {
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
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  .cards {
    margin: $gap-1;
  }
}
</style>
