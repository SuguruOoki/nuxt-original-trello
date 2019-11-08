<template>
  <div class="content">
    <div>
      <div id='example-3'>
        <input type="checkbox" id="todo" value="TODO" v-model="checkedColumns" @click="handleSearch">
        <label for="todo">TODO</label>
        <input type="checkbox" id="will" value="WILL" v-model="checkedColumns">
        <label for="will">WILL</label>
        <br>
        <span>Checked Columns: {{ checkedColumns }}</span>
      </div>
    </div>
    <div class="board-wrapper">
      <div v-for="key in cardContents" :key="key.id" class="card-column-wrapper">
        <CardColumn :columnTitle="key.title"/>
      </div>
    </div>
  </div>
</template>

<script>
import CardColumn from '~/components/CardColumn.vue'

export default {
  components: {
    CardColumn
  },
  data() {
    return {
      cardContents: [
        {
          title: 'TODO'
        },
        {
          title: 'WILL'
        }
      ],
      checkedColumns: [],
      firstCardContents: this.cardContents
    }
  },
  methods: {
    handleSearch() {
      console.log(this.checkedColumns)
      if (this.checkedColumns === []) return firstCardContents
      this.cardContents = this.cardContents.filter((cardContent) => {
        cardContent === this.checkedColumns[0]
      })
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
