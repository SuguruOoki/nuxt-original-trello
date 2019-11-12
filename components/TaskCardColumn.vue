<template>

  <div class="container-card-column">
    <div>
      <h3>{{ columnTitle }}</h3>
    </div>
    <div v-for="key in sample" :key="key.id" class="card-gap">
      <div class="task-card-flex-row">
        <TaskCard :cardContent="key"/>
        <AppButton buttonText="更新" backgroundColor="orange" width="10%"/>
        <AppButton buttonText="削除"  width="10%"/>
      </div>
    </div>
    <div class="button-add">
        <span>コメント</span>
        <input type="text" v-model.lazy="taskInputContent" />
        <!-- <AppButton buttonText="追加" @click="handleInputStatus" backgroundColor="green" /> -->
        <AppButton buttonText="追加" @click="handleAddTask(taskInputContent)"  backgroundColor="blue" />
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
  methods: {
    handleAddTask: function() {
      if (this.taskInputContent !== '') {
        console.log(this.taskInputContent)
        this.sample.push(this.taskInputContent)
      }
    },
    handleInputStatus() {
      this.inputStatus = !this.inputStatus
    }
  },
  components: {
    AppButton,
    TaskCard
  },
  data() {
    return {
      taskInputContent: '',
      inputStatus: false,
      sample: ['1', '2', '3', '4', '5']
    }
  }
}
</script>

<style lang="scss" scoped>
$gap-1: 8px;

.container-card-column {
  background-color: #ebecf0;
  border-radius: 4px;
  min-height: 100px;
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}
.task-card-flex-row {
  display: flex;
  flex-direction: row;
}

.button-add {
  margin: 12px;
}

.card-gap {
  padding: 16px;
}
</style>
