<script setup>

import Team from "@/components/Team.vue";

const {match} = defineProps(['match']);

</script>

<template>
  <div class="card match-card">
    <div class="card-body">
      <small class="text-muted">
        {{ match.subtitle }} ({{ match.format_str }}) - {{ match.status_str }}
      </small>
      <div class="mt-2">
        <Team :team="match.teama" class="mb-2"/>
        <Team :team="match.teamb"/>
      </div>
      <small class="mt-2">
        <b>{{ match.result }}</b>
      </small>
    </div>
  </div>
</template>

<style scoped>

</style>