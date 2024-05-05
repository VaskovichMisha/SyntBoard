<template>
  <div class="radio">
    <input
        type="radio"
        :id="'radio_' + radio.id"
        :name="name"
    />
    <label :for="'radio_' + radio.id">
      {{ radio.label }}
    </label>
  </div>
</template>

<script>
export default {
  props: {
    radio: Object,
    name: String
  }
}
</script>

<style lang="scss" scoped>
@import "radio";
</style>