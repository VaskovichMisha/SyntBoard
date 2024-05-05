<template>
  <div class="button" :class="color">
    {{ text }}
  </div>
</template>

<script>
export default {
  props: {
    text: {
      type: String
    },
    color: {
      type: String
    }
  }
}
</script>

<style lang="scss" scoped>
@import "button";
</style>