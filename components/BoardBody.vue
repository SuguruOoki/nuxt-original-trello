<template>
  <div class="content">
    <div>
      <!-- <div id='example-3'>
        <input type="checkbox" id="todo" value="TODO" v-model="checkedColumns" @click="handleSearch">
        <label for="todo">TODO</label>
        <input type="checkbox" id="will" value="WILL" v-model="checkedColumns" @click="handleSearch">
        <label for="will">WILL</label>
        <br>
        <span>Checked Columns: {{ checkedColumns }}</span>
      </div> -->
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
    <div class="board-wrapper">
      <div v-for="key in cardContents" :key="key.id" class="card-column-wrapper">
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

<style lang="scss">
$gap-1: 8px;
$gap-2: 16px;

.content {
  width: 100%;
  background-color: transparent;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  .board-wrapper {
    display: flex;
    flex-direction: row;
    justify-content: flex-start;
    margin: $gap-2;
    .card-column-wrapper {
      margin: 0 $gap-2;
    }
  }
  .flex {
    display: flex;
    flex-direction: column;
  }
}

.title {
  color: #ffffff;
}
</style>
