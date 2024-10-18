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
  { id: 2, name: 'Zachy Kurt', dachart: 'Flachdach', preis: '15,000 €', kWp: '8 kWp', speicher: '14 kWh', charging:'Ja', wallbox: 'Nein', status: 'Folgetermin' }
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

  .table-body{
    display:flex;
    justify-content: space-between;
    flex-direction: column;
  }
 /*.table-head{
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: #EDEDED;
  font-weight: 400;
  z-index: 1;
  height:91px;
  width:1366px;
 
  
 }

  .table-head th{
    padding: 5px; 
    text-align: center; 
    font-weight: 500;
}

  thead {
    text-align: center;
  }

    .table-head th {
        width: 150px; 
    }

  .table-head th:nth-child(8){
      padding-right:40px;
  }

  table {
    width: 100%; 
    width:1366px;
    border-collapse: collapse; 
    z-index: 1;
    position: relative;
  }

  .table-container {
    position: relative;
    display: flex;
    flex-direction: column;
    justify-content: center; 
    width: 1366px;
    width: 100%; 
    font-size: 17px;
    font-weight: 400;
    opacity: 50%;
    margin-top:10px;
    z-index: 1;
    overflow: visible;
    
  }

  .table-container table {
    align-self: flex-start; 
    width: 100%; 
    border-collapse: collapse;
    position: relative;
    border-radius: 30px 30px 0 0; 
    overflow: hidden; 
    margin-left:-10px;
}


 
  .table-container table {
      border: 1px solid #EDEDED; 
  }*/
</style>
