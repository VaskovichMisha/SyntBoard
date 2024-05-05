<template>
  <div class="distribution-select">
    <div
        @click="selectOpen = !selectOpen"
        class="distribution-select__selected"
    >
      {{ selectedChanged ? selectedChanged : selected }}
      <img
          :class="{ 'rotate-180': selectOpen }"
          src="@/assets/svg/arrow.down.svg"
          alt="arrow down"
      >
    </div>
    <div
        v-if="selectOpen"
        class="distribution-select__list"
    >
      <span
          v-for="item in selectData"
          @click="changeSelected(item)"
          class="distribution-select__item"
      >
        {{ item.text }}
      </span>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    selectData: Array,
    selected: String
  },
  data() {
    return {
      selectOpen: false,
      selectedChanged: ''
    }
  },
  methods: {
    changeSelected(item) {
      this.selectedChanged = item.text
      this.selectOpen = false
    }
  }
}

</script>

<style lang="scss" scoped>
@import "select";
</style>