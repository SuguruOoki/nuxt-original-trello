<template>
  <div class="container-card">
    <div>
      <h3>{{ columnTitle }}</h3>
    </div>
    <div v-for="key in sample" :key="key" class="flex-column card-gap">
      <div>
        <TaskCard :cardContent="key"/>
      </div>
      <div class="flex-row">
        <AppButton buttonText="更新" backgroundColor="orange"/>
        <AppButton buttonText="削除" />
      </div>
    </div>
  </div>
</template>
<script>
import TaskCard from './TaskCard.vue'
import AppButton from './AppButton.vue'

export default {
  props: {
    columnTitle: {
      type: String,
      require: true
    }
  },
  components: {
    AppButton,
    TaskCard
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
.flex-column {
  display: flex;
}
.flex-row {
  display: flex;
  flex-direction: row;
}

.card-gap {
  padding: 16px;
}
</style>
