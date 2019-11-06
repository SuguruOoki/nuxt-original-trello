<template>
  <div class="content">
    <div v-for="key in cardContent" :key="key.id" class="board-wrapper">
      <CardColumn :title="title"/>
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
      cardContent: [
        {
          title: 'TODO'
        },
        {
          title: 'WILL'
        }
      ]
    }
  }
}
</script>

<style lang="scss">
.content {
  width: 100%;
  background-color: transparent;
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  .board-wrapper {
    padding: 8px;
  }
}

.title {
  color: #ffffff;
}
</style>
