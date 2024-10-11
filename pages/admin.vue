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

      <div class="table-container" >
       <table>
        <thead>
          <tr class="table-head">
            <th style="margin-right: 100px;">Name</th>
            <th>Dachart</th>
            <th>Preis</th>
            <th>kWp</th>
            <th>Speicher</th>
            <th>Wallbox</th>
            <th>Status</th>
            <th style="margin-right: 50px;" >Aktionen</th>
          </tr>
        </thead>
        <!--Einfügen der Customer Row Component-->

        <tbody>
          <!-- <customer-row
            v-for="customer in customers"
            :key="customer.id"
            :customer="customer"
            @edit="editCustomer"
            @clone="cloneCustomer"
            @delete="deleteCustomer"
            /> -->
        </tbody>
       </table>
      </div>
    </div>
</template>
  


<script setup>
  import { ref } from 'vue';
  import CustomerRow from '~/components/CustomerRow.vue';
  import SearchBar from '~/components/SearchBar.vue';
  import FilterOptions from '~/components/FilterOptions.vue';
  import AddCustomer from '~/components/AddCustomer.vue';
  
  // Testkunde
  const customers = ref([
  { id: 1, name: 'John Doe', dachart: 'Flachdach', preis: '15,000 €', kWp: 8, speicher: 'Ja', wallbox: 'Nein', status: 'Deal' }
  ]);


  

  const editCustomer = (customer) =>{
    // TODO
  }

  const cloneCustomer = (customer) =>{
    // TODO
  }

  const deleteCustomer = (customer) =>{
    // TODO
  }

    
  const totalCustomers = ref(25); // Beispielnummer

  
  </script>



<style scoped>

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

 .table-head{
  display: flex;
  justify-content: space-between;
  align-items: center;
  text-align: center;
  gap:70px;
  border-radius: 5px;
  background-color: #EDEDED;
  font-weight: 400;
  
 }

  tbody {
    text-align: center;
  }

  th {
    padding: 10px; /* Adds padding to the header cells */
    
    text-align: center; /* Centers the text inside each header cell */
  }

  thead {
    text-align: center;
  }

  table {
    width: 80%; /* Adjusts the width of the table, can be changed as needed */
    border-collapse: collapse; /* Ensures the table cells share borders */
  }

  .table-container {
    display: flex;
    justify-content: center; /* Centers the table horizontally */
    width: 1288px;
    width: 100%; /* Ensures the container spans the entire width of the page */
    font-size: 17px;
    font-weight: 400;
    opacity: 50%;
    margin-top:30px;
    
  }
</style>
