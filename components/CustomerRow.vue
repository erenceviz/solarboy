<template>
  <tr class="table-row">
    <td class="name-content">
      {{ customer.name }}
      <button class="name-button"></button>
    </td>

    <td class="table-content">
      <button class="roof-icon"></button>
      {{ customer.dachart }}
    </td>

    <td class="table-content">
      <button class="price-icon"></button>
      {{ customer.preis }}
    </td>

    <td class="table-content">
      <button class="solar-icon"></button>
      {{ customer.kWp }}
    </td>

    <td class="table-content">
      <button class="archive-icon"></button>
      {{ customer.speicher }}
      <button class="charging-icon"></button>
      {{ customer.charging }}
    </td>

    <td class="table-content">
      <button class="wallbox-icon"></button>
      {{ customer.wallbox }}
    </td>

    <td class="deal-content" :style="getStatusStyle(customer.status)">
      {{ customer.status }}
    </td>

    <td class="table-buttons">
      <button @click="editCustomer" class="edit-button">Edit</button>
      <button @click="$emit('clone', customer)" class="clone-button">Clone</button>
      <button @click="$emit('delete', customer)" class="delete-button">Delete</button>
    </td>
  </tr>

  <!-- Conditionally render the CustomerPopup -->
  <CustomerPopup
    v-if="isPopupVisible"
    :isVisible="isPopupVisible"
    title="Neuen Kunden anlegen"
    @close="closePopup"
    @save="saveCustomer"
  />
</template>

<script setup>
import { ref, defineProps } from 'vue';
import CustomerPopup from './CustomerPopup.vue';

const isPopupVisible = ref(false);
const filterHeight = '30px'; // Set filter height

const filterStyles = {
  'Deal': { backgroundColor: '#CCFAF1', borderColor: '#A5F1E1', color: '#0A6860', height: filterHeight, width: '52px', marginLeft: '0px' },
  'Offen': { backgroundColor: '#FAE7FF', borderColor: '#F5D0FF', color: '#9E15AC', height: filterHeight, width: '59px', marginLeft: '0px' },
  '1. Termin': { backgroundColor: '#FFECD5', borderColor: '#F4E3CD', color: '#C8501D', height: filterHeight, width: '82px', marginLeft: '-25px' },
  'Folgetermin': { backgroundColor: '#FEF8C3', borderColor: '#F2ECB4', color: '#AE7736', height: filterHeight, width: '105px', marginLeft: '-50px' },
  'No Deal': { backgroundColor: '#FDE6EB', borderColor: '#FDD4DD', color: '#B7225F', height: filterHeight, width: '75px', marginLeft: '-15px' }
};

const props = defineProps({
  customer: {
    type: Object,
    required: true,
  },
});

const getStatusStyle = (status) => {
  return filterStyles[status] || {}; // return the style if it exists, or an empty object
};

const editCustomer = () => {
  isPopupVisible.value = true; // Open the CustomerPopup
};

// Function to close the popup
const closePopup = () => {
  isPopupVisible.value = false; // Close the CustomerPopup
};

// You should define the saveCustomer function as well, depending on your implementation
const saveCustomer = (customerData) => {
  // Handle the saving of the customer data here
};
</script>





<style scoped>



.table-row{
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  padding:30px 20px 30px 50px;
  align-items: center;
  max-width:1366px;
  margin-left:-10px;
}

.table-row:nth-child(even) {
  background-color: #F6F7F8;
}

.name-content {
  width: 150px; /* Adjust the width as necessary */
  white-space: nowrap; /* Prevent text from wrapping */
  overflow: hidden; /* Hide overflowed content */
  text-overflow: ellipsis; /* Show ellipsis if the text overflows */
  align-items: center; /* Ensure items are vertically aligned */
  display: flex; /* Use flexbox to align text and button */
  justify-content: space-between; /* Add spacing between text and button */
}
.table-content{
  text-align: center;
  padding-left:0px;
  position: relative;
  margin-right:10px;
  display:flex;
  justify-content: center;
  flex-direction: row;
  align-items: center;
  
}
.deal-content {
  display: flex;
  align-items: center;
  justify-content: center;
  margin-right:10px;
  border-radius: 5px;
  line-height: 30px;
  font-weight: 500;
  max-width: 105px; /* Set a minimum width */
  flex-shrink: 0; /* Prevent shrinking */
  flex-grow: 0; /* Prevent growing */
  white-space: nowrap; /* Prevent text from wrapping */
  text-align: center;
  padding: 0 10px; /* Add some padding for better text alignment */
}


td button{
  margin-right:7px;
}

.edit-button {
  background: url('@/assets/pencil.svg') no-repeat center center;
  background-size: contain;
  width: 24px; /* Set appropriate width */
  height: 24px; /* Set appropriate height */
  border: none;
  cursor: pointer;
  text-indent: -9999px; /* Hides the text */
  margin-right:15px;
}

.clone-button {
  background: url('@/assets/clone 1.svg') no-repeat center center;
  background-size: contain;
  width: 24px; /* Set appropriate width */
  height: 24px;;
  border: none;
  cursor: pointer;
  margin-right:15px;
  text-indent: -9999px; /* Hides the text */
}

.delete-button {
  background: url('@/assets/trash.svg') no-repeat center center;
  background-size: contain;
  width: 24px; /* Set appropriate width */
  height: 24px;
  border: none;
  cursor: pointer;
  text-indent: -9999px; /* Hides the text */
}

.name-button{
  background: url('@/assets/angle-small-left 1.svg') no-repeat center center;
  background-size: contain;
  width: 20px; /* Set appropriate width */
  height: 20px;
  border: none;
  cursor: pointer;
  text-indent: -9999px; /* Hides the text */
}


.roof-icon{
  background:url('@/assets/roof-6 1.svg');
  border:0;
  width:30px;
  height:30px;
  background-repeat: no-repeat;
  background-size:contain;
  cursor: pointer;
  margin-left:-20px;
  background-position: center;
}

.price-icon{
  background:url('@/assets/coins.svg');
  border:0;
  width:30px;
  height:30px;
  background-repeat: no-repeat;
  background-size:contain;
  cursor: pointer;
  margin-left:-40px;
  background-position: center;
}

.solar-icon{
  background:url('@/assets/solar-panel.svg');
  border:0;
  width:30px;
  height:30px;
  background-repeat: no-repeat;
  background-size:contain;
  cursor: pointer;
  margin-left:-40px;
  background-position: center;
}

.archive-icon{
  background:url('@/assets/archive.svg');
  border:0;
  width:30px;
  height:30px;
  background-repeat: no-repeat;
  background-size:contain;
  cursor: pointer;
  margin-left:-40px;
  background-position: center;
}

.charging-icon{
  background:url('@/assets/charging-station 1.svg');
  border:0;
  width:30px;
  height:30px;
  background-repeat: no-repeat;
  background-size:contain;
  cursor: pointer;
  margin-left:20px;
  background-position: center;
}

.wallbox-icon{
  background:url('@/assets/expense 1.svg');
  border:0;
  width:30px;
  height:30px;
  background-repeat: no-repeat;
  background-size:contain;
  cursor: pointer;
  margin-left:-20px;
  background-position: center;
}

.table-buttons{
  margin-left:-50px;
  margin-right: 20px;
}



</style>