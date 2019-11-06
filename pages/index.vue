<template>
  <div class="container">
    <BoardBody/>
  </div>
</template>

<script>
import BoardBody from '~/components/BoardBody.vue'

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
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  color: #ffffff;
}
</style>
