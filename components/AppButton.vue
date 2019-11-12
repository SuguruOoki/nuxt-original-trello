<template>
  <div class="button" :style="styles">{{ buttonText }}</div>
</template>

<script>
export default {
  props: {
    buttonText: {
      type: String,
      require: true
    },
    backgroundColor: {
      type: String,
      require: false,
      default: 'red'
    },
    width: {
      type: String,
      require: false,
      default: '100%'
    }
  },
  computed: {
    styles() {
      return {
        'background-color': this.backgroundColor,
        'width': this.width
      }
    }
  }
}
</script>

<style lang="scss" scoped>
.button {
  background-color: #ffffff;
  color: #172b4d;
  border-radius: 4px;
  padding: 12px 16px;
}
</style>
