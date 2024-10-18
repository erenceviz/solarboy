<!-- CustomerRow als Component für die Tabelle-->

<template>
  <div>
    <tr class="table-row">
      <div>
        <td>{{ customer.name }}</td>
      </div>

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

      <td  class="deal-content" :style="getStatusStyle(customer.status)">
        
        {{ customer.status }}
      </td>

      <td class="table-buttons">
        
          <button @click="$emit('edit', customer)">Edit</button>
          <button @click="$emit('clone', customer)">Clone</button>
          <button @click="$emit('delete', customer)">Delete</button>
        
      </td>
    </tr>
  </div>
</template>


<script setup>
import { defineProps } from 'vue';

// Define filterHeight
const filterHeight = '30px'; // or any other value you'd like to set

const filterStyles = {
  'Deal': { backgroundColor: '#CCFAF1', borderColor: '#A5F1E1', color: '#0A6860', height: filterHeight, width: '52px' },
  'Offen': { backgroundColor: '#FAE7FF', borderColor: '#F5D0FF', color: '#9E15AC', height: filterHeight, width: '59px' },
  '1. Termin': { backgroundColor: '#FFECD5', borderColor: '#F4E3CD', color: '#C8501D', height: filterHeight, width: '82px' },
  'Folgetermin': { backgroundColor: '#FEF8C3', borderColor: '#F2ECB4', color: '#AE7736', height: filterHeight, width: '105px' },
  'No Deal': { backgroundColor: '#FDE6EB', borderColor: '#FDD4DD', color: '#B7225F', height: filterHeight, width: '75px' }
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

</script>




<style scoped>



.table-row{
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  padding:30px 20px 30px 40px;
  align-items: center;
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
.deal-content{
  position: relative;
      margin-right:20px;
      border-radius: 5px;
      text-align: center;
      line-height: 30px;
      font-weight:500;
      display:flex;
      justify-content: center;
      flex-direction: row;
      align-items: center;
}

td button{
  margin-right:7px;
}

.roof-icon{
  background:url('@/assets/roof-6 1.svg');
  border:0;
  width:30px;
  height:30px;
  background-repeat: no-repeat;
  background-size:contain;
  cursor: pointer;
  margin-left:60px;
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
}

button{
  margin-right: 5px;
}

</style>