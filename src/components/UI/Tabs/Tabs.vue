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
  data() {
    return {
      selectedTab: 0,
      tabs: [
        { title: 'Graph', id: 0},
        { title: 'Heatmap', id: 1},
        { title: 'Diagram', id: 2},
      ]
    }
  },
  methods: {
    openTab(tab) {
      this.selectedTab = tab.id
    }
  },
  mounted() {

  }
}
</script>

<style lang="scss" scoped>
@import "tabs";
</style>