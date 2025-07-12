<template>
  <div class="header">
    <div class="label-col"></div>
    <div
      v-for="month in months"
      :key="month"
      class="month-group"
      :style="{ gridTemplateColumns: 'repeat(4, 1fr)' }"
    >
      <div v-for="week in 4" :key="week" class="week-cell">
        {{ monthNames[month - 1] }} Week {{ week }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ['start', 'end'],
  computed: {
    months() {
      const arr = [];
      for (let m = this.start; m <= this.end; m++) arr.push(m);
      return arr;
    },
    monthNames() {
      return ['January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'September', 'October', 'November', 'December'];
    }
  }
};
</script>

<style scoped>
.header {
  display: grid;
  grid-template-columns: 200px repeat((end - start + 1) * 4, minmax(100px, 1fr));
}
.week-cell {
  padding: 8px;
  border: 1px solid #ccc;
  text-align: center;
  background: #f0f0f0;
}
</style>
