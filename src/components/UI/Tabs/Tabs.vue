<template>
  <div class="tabs">
    <div
        v-for="tab in tabs"
        :key="tab.id"
        @click="openTab(tab)"
        :class="{ 'active': tab.id === selectedTab }"
        class="tabs__tab"
    >
      <span>{{ tab.title }}</span>
    </div>
  </div>
</template>

<script>

export default {
  props: {
    tabs: Array
  },
  data() {
    return {
      selectedTab: 0,
    }
  },
  methods: {
    openTab(tab) {
      this.selectedTab = tab.id
      this.$emit('change-tab', tab.id)
    }
  },
  mounted() {

  }
}
</script>

<style lang="scss" scoped>
@import "tabs";
</style>