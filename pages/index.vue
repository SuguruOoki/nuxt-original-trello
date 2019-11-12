<template>
  <div class="container">
    <BoardBody />
  </div>
</template>

<script>
import BoardBody from '~/components/BoardBody.vue'
// import CardSearch from '~/components/CardSearch.vue'

export default {
  components: {
    BoardBody
  }
}
</script>

<style>
.container {
  display: flex;
  background-color: transparent;
  flex-direction: column;
  justify-content: space-between;
  /* align-items: center; */
  text-align: center;
}

.title {
  color: #ffffff;
}
</style>
