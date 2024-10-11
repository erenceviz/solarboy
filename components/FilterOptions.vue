<template>
  <div class="filter-status" :style="{ width: buttonWidth }">
    <div class="filter-content">
      <span>Status</span>
      <span v-if="selectedFilters.length > 0">{{ selectedFilters.join(' ') }}</span>
    </div>

    <div class="filter-buttons">
      <button @click="toggleFilterOptions" class="toggle-filters">
        <i class="icon-dropdown"></i>
      </button>
      <button @click="clearFilters" class="clear-filters">
        <i class="icon-clear"></i>
      </button>
    </div>

    <div v-if="filterVisible" class="filter-options">
      <ul>
        <li v-for="(value, key) in filters" :key="key">
          <input type="checkbox" v-model="filters[key]" :id="`filter-${key}`" />
          <label :for="`filter-${key}`">{{ key }}</label>
        </li>
      </ul>
    </div>
  </div>
</template>



<script setup>
import { ref, computed } from 'vue';

const buttonWidth = computed(() => {
  const baseWidth = 162; // Initial width
  const maxWidth = 319; // Maximum width
  const additionalWidth = selectedFilters.value.length * 10; // Increase width based on the number of filters
  return `${Math.min(baseWidth + additionalWidth, maxWidth)}px`;
});

// Filter initial state
const filters = ref({
  Deal: false,
  Offen: false,
  '1.Termin': false,
  Folgetermin: false,
  'NoDeal': false,
});

const filterVisible = ref(false);

const toggleFilterOptions = () => {
  filterVisible.value = !filterVisible.value;
};

const selectedFilters = computed(() => {
  return Object.keys(filters.value).filter(key => filters.value[key]);
});

const clearFilters = () => {
  filterVisible.value = !filterVisible.value;
  Object.keys(filters.value).forEach(key => {
    filters.value[key] = false;
  });
};

const applyFilter = (filter) => {
  console.log(`Applied filter: ${filter}`);
};
</script>



<style scoped>

    .filter-status{
        /* height: 50px;
        width: 202px;
        margin-top:30px;
        border-width: 1px;
        border-radius: 500px;
        border-color: #EDEDED;
        border: 1px solid #EDEDED; */
        display: flex;
        align-items: center;
        justify-content: space-between;
        height: 48px;
        border-radius: 500px;
        border: 1px solid #EDEDED;
        padding: 0 20px;
        font-size: 17px;
        font-weight: 500;
        opacity:50%;
        background-color: #fff;
        box-shadow: 0px 1px 2px 0px #00000005;
        cursor: pointer;
        transition: width 0.3s ease;
        position: relative;
        margin-top:30px;
        margin-left:-60px;
    }

    .filter-options {
      position: absolute;
      top: 55px; /* Adjust vertical placement */
      left: 0; /* Align with the filter button */
      border-radius: 15px;
      border: 1px solid #ccc;
      padding: 10px;
      width: 240px;
      margin-right:100px;
      display: flex;
      flex-direction: column;
      flex-wrap: nowrap; /* Ensure items stay on the same line */
      overflow: hidden; /* Hide overflow */
      z-index: 10; /* Ensure it appears on top */
      background-color: rgba(255, 255, 255, 0.9);
      
    }

    .filter-content {
        display: flex;
        align-items: center;
        gap: 5px; /* Space between 'Status' and selected filters */
        white-space: nowrap; /* Prevent wrapping to the next line */
        overflow: hidden; /* Hide overflow */
        max-width: calc(100% - 80px); /* Adjust based on button sizes */
    }

  .filter-buttons {
        display: flex;
        align-items: center;
        gap: 10px; /* Space between the clear and toggle buttons */
    }

  .filter-options ul {
        list-style-type: none; /* Removes bullet points */
        padding: 0;            /* Removes any padding from the ul */
        
    }

  .filter-options li {
        margin-bottom: 5px;    /* Adds some space between the filter items */
        display:flex;
        flex-wrap:nowrap;
    }

  /* Background colors for each filter option */
  .filter-options li:nth-child(1) {
    background-color: #CCFAF1;
    border-color: #A5F1E1; /* Red */
  }

  .filter-options li:nth-child(2) {
    background-color: #FAE7FF; /* Blue */
    border-color: #F5D0FF;
  }

  .filter-options li:nth-child(3) {
    background-color: #FFECD5; /* Green */
    border-color: #F4E3CD;
  }

  .filter-options li:nth-child(4) {
    background-color: #FEF8C3; /* Yellow */
    border-color: #F2ECB4;
  }

  
</style>