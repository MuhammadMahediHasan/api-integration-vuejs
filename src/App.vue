<script setup>
import Header from "@/components/Header.vue";
import Footer from "@/components/Footer.vue";
import MatchCard from "@/components/MatchCard.vue";

import {reactive, ref} from "vue";
import axios from "axios";

const apiBaseURL = 'https://rest.entitysport.com/v2';
const matches = ref([]);
const pages = reactive({
  currentPage: 0,
  totalPage: 0,
});

const fetchMatches = (perPage = 1) => {
  axios.get(`${apiBaseURL}/matches/?status=2&paged=${perPage}&token=ec471071441bb2ac538a0ff901abd249`).then(({data}) => {
    matches.value.push(...data.response.items);
    pages.totalPage = data.response.total_pages;
    pages.currentPage += 1;
  });
}
fetchMatches();
</script>

<template>
  <div>
    <Header/>
    <div class="row mb-4">
      <template v-for="match in matches">
        <div class="col-md-6 pb-4">
          <MatchCard :match/>
        </div>
      </template>
    </div>
    <div v-if="pages.totalPage !== pages.currentPage" class="row mt-4">
      <div class="col text-center">
        <button class="btn btn-outline-secondary" @click="fetchMatches(pages.currentPage + 1)">
          See More
        </button>
      </div>
    </div>
    <Footer/>
  </div>
</template>
