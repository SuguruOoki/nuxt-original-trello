<template>
  <div class="board-body-content">
    <div class="cardcolumn-search-flex">
      <div v-for="(cardContent, i) in cardContents" :key="i">
        <input
          :id="'cardContent' + i"
          type="checkbox"
          :value="cardContent"
          v-model="checkedColumns"
          @click="handleSearch"
        >
        <label :for="'cardContent' + i">{{ cardContent }}</label>
      </div>
    </div>
    <div class="task-cards-wrapper">
      <div v-for="key in cardContents" :key="key.id" class="task-cards-content">
        <TaskCardColumn :columnTitle="key"/>
      </div>
    </div>
  </div>
</template>

<script>
import TaskCardColumn from '~/components/TaskCardColumn.vue'

export default {
  components: {
    TaskCardColumn
  },
  data() {
    return {
      cardContents: [
          'TODO',
          'WILL'
      ],
      // cardContents: [
      //   {
      //     title: 'TODO'
      //   },
      //   {
      //     title: 'WILL'
      //   }
      // ],
      checkedColumns: [],
      selectedColumns: this.cardContents,
      firstCardContents: this.cardContents
    }
  },
  methods: {
    handleSearch() {
      console.log(this.checkedColumns)
      // this.selectedColumns = this.cardContents.filter((cardContent) => {
      //   return cardContent === this.card
      // })

      // if (this.checkedColumns === []) return firstCardContents

      // this.cardContents = this.cardContents.filter((cardContent) => {
      //   // console.log(cardContent.title)
      //   console.log(cardContent.title)
      //   console.log(this.checkedColumns)

      //   cardContent.title === this.checkedColumns
      // })
    }
  }
}
</script>

<style lang="scss" scoped>
$gap-1: 8px;
$gap-2: 16px;

.board-body-content {
  background-color: transparent;
  display: flex;
  flex-direction: column;

  .cardcolumn-search-flex {
    display: flex;
    flex-direction: row;
  }
}
.task-cards-wrapper {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  margin: 24px;
  .task-cards-content {
    max-width: 300px;
  }
}


.title {
  color: #ffffff;
}

@media screen and (max-width: 768px){
  .content {
    width: 80%;
  }
}
</style>
