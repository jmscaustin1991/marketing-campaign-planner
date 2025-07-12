<template>
  <div class="calendar">
    <Header :start="startMonth" :end="endMonth" />
    <div class="grid">
      <CampaignRow
        v-for="camp in campaigns"
        :key="camp.id"
        :campaign="camp"
        @update="onUpdate"
      />
    </div>
    <Legend />
    <PdfExporter ref="exporter" :refDom="\$el" />
  </div>
</template>

<script>
import Header from './Header.vue';
import CampaignRow from './CampaignRow.vue';
import Legend from './Legend.vue';
import PdfExporter from './PdfExporter.vue';
import scheduleData from '../data/schedule.json';

export default {
  components: { Header, CampaignRow, Legend, PdfExporter },
  data() {
    return {
      campaigns: scheduleData.campaigns,
      startMonth: 7,
      endMonth: 12
    };
  },
  methods: {
    onUpdate(updated) {
      this.campaigns = updated;
    },
    exportPDF() {
      this.$refs.exporter.generatePDF();
    }
  }
};
</script>
