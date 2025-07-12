<template>
  <div
    class="content-card"
    :class="card.type"
    draggable="true"
    @dblclick="editCard"
  >
    {{ card.label }}
    <button @click.stop="deleteSelf">×</button>
  </div>
</template>

<script>
export default {
  props: ['card'],
  methods: {
    editCard() {
      const newLabel = prompt('Edit label', this.card.label);
      if (newLabel) this.$emit('updateCard', { ...this.card, label: newLabel });
    },
    deleteSelf() {
      this.$emit('deleteCard', this.card.id);
    }
  }
};
</script>

<style scoped>
.content-card { padding: 8px; border-radius: 4px; box-shadow: 0 1px 3px rgba(0,0,0,0.2); margin: 4px 0; }
.email { border-left: 4px solid #007bff; }
.social { border-left: 4px solid #28a745; }
.newsletter { border-left: 4px solid #ffc107; }
</style>
