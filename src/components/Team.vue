<script setup>
const {team} = defineProps(['team']);
</script>

<template>
  <div class="d-flex justify-content-between">
    <div>
      <img class="team-flag" :src="team.logo_url" alt=""/>
      <span>{{ team.name }}</span>
    </div>
    <div>
      <span class="score ms-2">
        <template v-if="team.scores">
          {{ team.scores }} ({{ team.overs }})
        </template>
        <template v-else>
          Yet to bat
        </template>
      </span>
    </div>
  </div>
</template>

<style scoped>

</style>