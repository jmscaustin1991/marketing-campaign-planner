<template>
  <div class="legend">
    <div><span class="box email"></span> Email</div>
    <div><span class="box social"></span> Social</div>
    <div><span class="box newsletter"></span> Newsletter</div>
    <div><span class="connector-icon"></span> Cross-promotion connector</div>
  </div>
</template>

<style scoped>
.legend { position: absolute; bottom: 0; width: 100%; background: #fff; padding: 8px; display: flex; gap: 16px; }
.box { display: inline-block; width: 16px; height: 16px; margin-right: 4px; border-radius: 2px; }
.email { background: #007bff; }
.social { background: #28a745; }
.newsletter { background: #ffc107; }
.connector-icon { width: 24px; height: 4px; background: #333; display: inline-block; }
</style>
