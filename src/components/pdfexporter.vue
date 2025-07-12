<template>
  <button @click="generatePDF">Export as PDF</button>
</template>

<script>
import html2canvas from 'html2canvas';
import jsPDF from 'jspdf';
export default {
  props: ['refDom'],
  methods: {
    async generatePDF() {
      // Capture calendar container
      const canvas = await html2canvas(this.refDom);
      const imgData = canvas.toDataURL('image/png');
      const pdf = new jsPDF({ orientation: 'landscape' });
      pdf.addImage(imgData, 'PNG', 0, 0, pdf.internal.pageSize.getWidth(), pdf.internal.pageSize.getHeight());
      pdf.save('campaign-planner.pdf');
    }
  }
};
</script>
