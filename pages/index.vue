<template>
  <div class="container">
    <div class="header">
      <h3 class="title">nuxt-trello</h3>
    </div>
    <div class="content">
      <div class="board-wrapper">
        <CardColumn></CardColumn>
      </div>
    </div>
    <div class="footer">footer</div>
  </div>
</template>

<script>
import CardColumn from '~/components/CardColumn.vue'

export default {
  components: {
    CardColumn
  }
}
</script>

<style>
.container {
  display: flex;
  background-color: #0079bf;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  color: #ffffff;
}
</style>
