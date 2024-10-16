<template>
  <div class="filter-status" :style="{ width: buttonWidth }">
    <div class="filter-content">
      <span style="opacity: 50%;">Status</span>
      <span  v-if="selectedFilters.length > 0">
        <span v-for="filter in selectedFilters" :key="filter" :style="filterStyles[filter]" class="selected-filter">
          {{ filter }}
        </span>
      </span>
    </div>

    <div class="filter-buttons">
      <button @click="toggleFilterOptions" class="toggle-filters">
        <!-- <span class="icon-dropdown"></span> -->
      </button>
      <button @click="clearFilters" class="clear-filters">
        <!-- <i class="icon-clear"></i> -->
      </button>
    </div>

    <div v-if="filterVisible" class="filter-options">
      <ul>
        <li v-for="(value, key) in filters" :key="key">
          <input type="checkbox" v-model="filters[key]" :id="`filter-${key}`" class="custom-checkbox" />
          <span class="custom-label"></span>
          <label :for="`filter-${key}`" :style="filterStyles[key]" >{{ key }} </label>
        </li>
        <div class="toggle-all">
          <span>Alle auswählen</span>
          <input @click="toggleAllOptions" type="checkbox" class="custom-checkbox2"/>
          <span class="custom-label2"></span>
        </div>
        
        
      </ul>
    </div>
  </div>
</template>



<script setup>
import { ref, computed } from 'vue';

const buttonWidth = computed(() => {
  const baseWidth = 162; // Initial width
  const maxWidth = 319; // Maximum width
  const additionalWidth = selectedFilters.value.length * 35; // Increase width based on the number of filters
  return `${Math.min(baseWidth + additionalWidth, maxWidth)}px`;
});

// Filter initial state
const filters = ref({
  Deal: false,
  Offen: false,
  '1. Termin': false,
  Folgetermin: false,
  'No Deal': false,
});

const filterVisible = ref(false);
const allSelected = ref(false);

const toggleFilterOptions = () => {
  filterVisible.value = !filterVisible.value;
};

const selectedFilters = computed(() => {
  return Object.keys(filters.value).filter(key => filters.value[key]);
});

const toggleAllOptions = () => {
  allSelected.value = !allSelected.value;
  Object.keys(filters.value).forEach(key => {
    filters.value[key] = allSelected.value;
  });
};

const clearFilters = () => {
  if (filterVisible.value ){
    filterVisible.value = !filterVisible.value;
  }
  Object.keys(filters.value).forEach(key => {
    filters.value[key] = false;
  });
};

const applyFilter = (filter) => {
  console.log(`Applied filter: ${filter}`);
};

// Define styles for each filter
const filterStyles = {
  Deal: {
    backgroundColor: '#CCFAF1',
    borderColor: '#A5F1E1',
    color: '#0A6860',
    height:'31px',
    width:'52px',
    
  },
  Offen: {
    backgroundColor: '#FAE7FF',
    borderColor: '#F5D0FF',
    color: '#9E15AC',
    height:'31px',
    width:'59px'
  },
  '1. Termin': {
    backgroundColor: '#FFECD5',
    borderColor: '#F4E3CD',
    color: '#C8501D',
    height:'31px',
    width:'82px'
  },
  Folgetermin: {
    backgroundColor: '#FEF8C3',
    borderColor: '#F2ECB4',
    color: '#AE7736',
    height:'31px',
    width:'105px'
  },
  'No Deal': {
    backgroundColor: '#FDE6EB',
    borderColor: '#FDD4DD',
    color: '#B7225F',
    height:'31px',
    width:'75px'
  }
};

</script>



<style scoped>

  .toggle-filters{
    height: 8px; /* Adjust height if needed */
    width: 15px; /* Adjust width if needed */
    
    background-size: contain; /* Make sure the background fits */
    border: 0; /* Remove border */
    opacity: 50%; /* Set opacity */
    cursor: pointer; /* Change cursor to pointer on hover */
    background:url('C:\Users\Eren\Documents\Business\nuxt-project\assets\01 align center down.svg');
  }

  .clear-filters{
    height: 15px; /* Adjust height if needed */
    width: 15px; /* Adjust width if needed */
    
    background-size: contain; /* Make sure the background fits */
    border: 0; /* Remove border */
    /* Set opacity */
    cursor: pointer; /* Change cursor to pointer on hover */
    background:url('C:\Users\Eren\Documents\Business\nuxt-project\assets\cross-small 1.svg');
  }

  .toggle-all{
    display:flex;
    justify-content: space-between;
    margin-top: 30px;
    margin-bottom: 0px;
    
  }

  

  
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
        
        background-color: #fff;
        box-shadow: 0px 1px 2px 0px #00000005;
        cursor: pointer;
        transition: width 0.3s ease;
        position: relative;
        margin-top:30px;
        margin-left:-20px;
        margin-right:20px;
    }

    .filter-options {
      position: absolute;
      top: 55px; /* Adjust vertical placement */
      left: 0; /* Align with the filter button */
      border-radius: 15px;
      border: 1px solid #EDEDED;
      padding: 20px 20px 10px 20px;
      max-width: 198px;
      max-height:320px;
      margin-right:100px;
      display: flex;
      justify-content: space-between;
      flex-wrap:nowrap; 
      overflow: hidden; 
      
      z-index: 9999; /* Ensure it appears on top */
      background-color: rgba(255, 255, 255, 0.9);
      font-size: 14px;
      margin-top: 5px;
      
      transition: max-height 0.3s ease-in-out, opacity 0.3s ease-in-out;
      
    }

    

    .selected-filter{
      font-size:14px;
      margin-left: 0; 
      border-radius: 5px;
      text-align: center;
      line-height: 30px;
      font-weight:600 !important;
      display: inline-block;
      z-index: 100;
    }

    

    .filter-content {
        display: flex;
        align-items: center;
        gap:2px; /* Space between 'Status' and selected filters */
        white-space: nowrap; /* Prevent wrapping to the next line */
        overflow: hidden; /* Hide overflow */
        max-width: calc(100% - 60px); /* Adjust based on button sizes */
        z-index: 9999;
        
    }

    .filter-content span {
      margin-right: 8px; /* Add space between the selected filters */
      z-index: 9999;
     
    }

  .filter-buttons {
      display: flex; /* Use flexbox */
      justify-content: space-between; /* Space out buttons */
      align-items: center; /* Align items vertically centered */
      gap: 10px; /* Space between buttons */
    }

  .filter-options ul {
        list-style-type: none; /* Removes bullet points */
        padding: 0;  
        width:100%;
        margin-top:0px;
  }

  .filter-options li {
        margin-bottom: 10px;    
        display:flex;
        flex-wrap:nowrap;
        align-items: start;
    }

    /*.filter-options li {
      display: flex;
      
      justify-content: flex-start;
      margin-bottom: 5px;
    }*/
    
    .filter-options input{
      z-index:3;
      align-items: flex-start;
      border: 1px solid #EDEDED;
    }
    
    .filter-options label {
      margin-left: 0; 
      border-radius: 5px;
      text-align: center;
      line-height: 30px;
      font-weight:500;
      
    }

  @media only screen and (max-width: 1366px) {
    .filter-options {
      width: 100%; /* Stretch filter options to full width */
      z-index: 9999;
    }
  
    .filter-options li {
      justify-content: flex-start; /* Keep items aligned to the left */
    }
  
    .filter-options ul, .filter-options li {
      flex-direction: row; /* Ensure checkbox and label are horizontal */
      width:100%;
      z-index: 9999;
    }
  
    /*.filter-options input[type="checkbox"] {
      margin-right: 10px; 
      margin-left: 0;
      border-radius: 3px;
      border: 1px solid #EDEDED;
      z-index: 9999;
      height:24px;
      width:24px;
      background-color: aqua;
    }*/

    .custom-checkbox{
      position: absolute; /* Hide default checkbox */
      opacity: 0; /* Hide it visually */
    }

    .custom-checkbox2{
      position: absolute; /* Hide default checkbox */
      opacity: 0; /* Hide it visually */
    }
    .custom-label {
      position: relative;
      padding-left: 30px; /* Space for the custom checkbox */
      cursor: pointer; /* Change cursor on hover */
      display: inline-block; /* To accommodate width and height */
      font-weight: 500; /* Optional styling */
      margin-top: 15px;
      margin-right:5px;
      
    }

    .custom-label::before {
      content: '';
      position: absolute;
      left: 0; /* Position to the left of the text */
      top:50%; /* Center vertically */
      transform: translateY(-50%); /* Adjust to center */
      width: 22px; /* Custom checkbox width */
      height: 22px; /* Custom checkbox height */
      border: 1px solid #EDEDED; /* Custom border color */
      border-radius: 3px; /* Rounded corners */
      background: white; /* Custom background */
      z-index: 0; /* Behind label text */
    }

    /* Change appearance when checked */
    .custom-checkbox:checked + .custom-label::before {
      background: #2A3F94; /* Change to your preferred color */
     
    }
    .filter-status {
      width: auto; /* Make sure the filter status adjusts to content */
    }

    .custom-label::after {
        content: '';
        position: absolute;
        left: 6px; /* Adjust to position it within the checkbox */
        top: 50%; /* Center vertically */
        transform: translateY(-50%); /* Adjust to center */
        width: 12px; /* Width of the checkmark */
        height: 12px; /* Height of the checkmark */
        background: url('C:\Users\Eren\Documents\Business\nuxt-project\assets\check-11 1.svg') no-repeat center center; /* Your SVG here */
        display: none; /* Hide by default */
        z-index: 1; /* Ensure it appears above the custom checkbox */
    }

    /* Show checkmark when checkbox is checked */
    .custom-checkbox:checked + .custom-label::after {
        display: block; /* Show checkmark */
    }


    .custom-label2 {
      position: relative;
      padding-left: 30px; /* Space for the custom checkbox */
      cursor: pointer; /* Change cursor on hover */
      display: inline-block; /* To accommodate width and height */
      font-weight: 500; /* Optional styling */
      margin-bottom:4px;
      margin-right:5px;
      
    }

    .custom-label2::before {
      content: '';
      position: absolute;
      left: 0; /* Position to the left of the text */
      top:50%; /* Center vertically */
      transform: translateY(-50%); /* Adjust to center */
      width: 22px; /* Custom checkbox width */
      height: 22px; /* Custom checkbox height */
      border: 1px solid #EDEDED; /* Custom border color */
      border-radius: 3px; /* Rounded corners */
      background: white; /* Custom background */
      z-index: 0; /* Behind label text */
    }

    .custom-label2::after {
        content: '';
        position: absolute;
        left: 6px; /* Adjust to position it within the checkbox */
        top: 50%; /* Center vertically */
        transform: translateY(-50%); /* Adjust to center */
        width: 12px; /* Width of the checkmark */
        height: 12px; /* Height of the checkmark */
        background: url('C:\Users\Eren\Documents\Business\nuxt-project\assets\check-11 1.svg') no-repeat center center; /* Your SVG here */
        display: none; /* Hide by default */
        z-index: 1; /* Ensure it appears above the custom checkbox */
    }

    .custom-checkbox2:checked + .custom-label2::after {
        display: block; /* Show checkmark */
    }

    

    
  }

  
</style>