<template>
  <div class="container">
    <div class="content">
      <div class="board-wrapper">
        <CardColumn/>
      </div>
    </div>
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
