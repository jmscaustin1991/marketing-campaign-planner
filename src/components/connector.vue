<template>
  <svg class="connector-layer">
    <path
      v-for="line in lines"
      :key="line.id"
      :d="line.path"
      stroke="#333" fill="none"
    />
  </svg>
</template>

<script>
export default {
  props: ['cards'],
  computed: {
    lines() {
      // Compute elbow connectors between cards sharing same label prefix
      return [];
    }
  }
};
</script>

<style scoped>
.connector-layer { position: absolute; top: 0; left: 0; width: 100%; height: 100%; pointer-events: none; }
</style>
