<template>
  <div class="campaign-row">
    <div class="label-col">
      <input v-model="local.name" @blur="emitUpdate" />
      <input type="date" v-model="local.startDate" @change="emitUpdate" />
      <button @click="removeCampaign">Delete</button>
      <button @click="addCard">Add Card</button>
    </div>
    <div class="cells">
      <!-- Render a cell for each week slot -->
      <div
        v-for="slot in totalSlots"
        :key="slot"
        class="cell"
        @drop.prevent="onDrop($event, slot)"
        @dragover.prevent
      >
        <ContentCard
          v-for="card in cardsInSlot(slot)"
          :key="card.id"
          :card="card"
          @dragstart.native="dragStart(card)"
          @updateCard="updateCard"
          @deleteCard="deleteCard"
        />
      </div>
    </div>
    <Connector :cards="local.cards" />
  </div>
</template>

<script>
import ContentCard from './ContentCard.vue';
import Connector from './Connector.vue';
export default {
  components: { ContentCard, Connector },
  props: ['campaign'],
  data() {
    return { local: JSON.parse(JSON.stringify(this.campaign)) };
  },
  computed: {
    totalSlots() {
      return (12 - 7 + 1) * 4;
    }
  },
  methods: {
    emitUpdate() {
      this.
      this.$emit('update', /* updated campaigns array */);
    },
    removeCampaign() {
      // Remove logic
    },
    addCard() {
      // Add card logic
    },
    cardsInSlot(slot) {
      // Return cards matching slot
      return this.local.cards.filter(c => /* matches */);
    },
    dragStart(card) {
      event.dataTransfer.setData('text/plain', card.id);
    },
    onDrop(event, slot) {
      const cardId = event.dataTransfer.getData('text');
      // Move card logic
      this.emitUpdate();
    },
    updateCard(updatedCard) {
      // Update label/date/type/custom
      this.emitUpdate();
    },
    deleteCard(cardId) {
      // Delete logic
      this.emitUpdate();
    }
  }
};
</script>

<style scoped>
.campaign-row { display: flex; }
.label-col { width: 200px; }
.cells { display: grid; grid-template-columns: repeat((12-7+1)*4, 1fr); }
.cell { min-height: 100px; border: 1px solid #eee; }
</style>
