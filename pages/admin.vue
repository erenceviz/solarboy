<template>
    <div>
      <div class="admin-header">

        <!-- Admin Panel Header erste Reihe-->
        <p class="customerlist">Ebene 2</p>

        <!-- Search-Bar -->
        <search-bar></search-bar>

        <!-- Filterbutton -->
        <filter-options></filter-options>

        <!-- Add-Customer -->
        <add-customer></add-customer>

      </div>
      
        <!-- Admin Panel Header zweite Reihe -->
        <div class="customerlist-info">
          <p class="kundenliste">Kundenliste</p>
          <p class="anzahl-customer">{{ totalCustomers }}</p>
        </div>
        
      <!-- Adminpanel Tabelle -->
      <table-head></table-head>

        <!--Einfügen der Customer Row Component-->
      
        <table class="table-body">
          <tbody>
            <customer-row
              v-for="customer in customers"
              :key="customer.id"
              :customer="customer"
              @edit="editCustomer"
              @clone="cloneCustomer"
              @delete="deleteCustomer"
              />
          </tbody>
       </table>
      
    </div>
</template>
  


<script setup>
  import { ref } from 'vue';
  import CustomerRow from '~/components/CustomerRow.vue';
  import SearchBar from '~/components/SearchBar.vue';
  import FilterOptions from '~/components/FilterOptions.vue';
  import AddCustomer from '~/components/AddCustomer.vue';
  import TableHead from '~/components/TableHead.vue';
  
  // Testkunde
  const customers = ref([
  { id: 1, name: 'John Doe', dachart: 'Flachdach', preis: '15,000 €', kWp: '8 kWp', speicher: '14 kWh', charging:'Ja', wallbox: 'Nein', status: 'Deal' },
  { id: 2, name: 'Zachy Kurt', dachart: 'Flachdach', preis: '15,000 €', kWp: '8 kWp', speicher: '14 kWh', charging:'Ja', wallbox: 'Nein', status: 'Folgetermin' },
  { id: 3, name: 'Martin Larsson', dachart: 'Flachdach', preis: '15,000 €', kWp: '8 kWp', speicher: '14 kWh', charging:'Ja', wallbox: 'Nein', status: '1. Termin' },
  { id: 4, name: 'Eren Ceviz', dachart: 'Flachdach', preis: '15,000 €', kWp: '8 kWp', speicher: '14 kWh', charging:'Ja', wallbox: 'Nein', status: 'Offen' },
  { id: 5, name: 'Jane Doe', dachart: 'Flachdach', preis: '15,000 €', kWp: '8 kWp', speicher: '14 kWh', charging:'Ja', wallbox: 'Nein', status: 'No Deal' },
  ]);



    
  const totalCustomers = ref(25); // Beispielnummer


  
  
</script>



<style scoped>

@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600;700&display=swap');


div, input, button,span {
  font-family: 'Poppins', sans-serif;
}


  .customerlist{
    font-weight: 500;
    font-size: 26px;
    line-height: 39px;
    margin-top: 34x;
    margin-left:40px;
  }

  .customerlist-info{
    display:flex;
    flex-direction: row;
    flex-wrap:nowrap;
    margin-top:-43px;
    margin-left:40px;
    gap: 10px;
    align-items: center;
  }

  .kundenliste{
    font-size:17px;
    font-weight:500;
    opacity: 50%;
  }

  .anzahl-customer{
    border-radius: 5px;
    background-color: #EDEDED;
    height:22px;
    width:38px;
    font-size:12px;
    font-weight:600;
    line-height: 18px;
    text-align: center;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .admin-header {
    display:flex;
    flex-direction: row;
    flex-wrap:nowrap;
    justify-content:space-between;
    
  }

  .table-body{
    display:flex;
    justify-content: space-between;
    flex-direction: column;
    overflow: auto; /* Enable scrolling */
    -webkit-overflow-scrolling: touch; /* Smooth scrolling on iOS */
    scrollbar-width: none;
  }
 
</style>
