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
        <div class="customer-list-info">
          <p>Kundenliste</p>
          <p>Total customers: {{ totalCustomers }}</p>
        </div>
        
      <!-- Adminpanel Tabelle -->

      <div>
       <table>
        <thead>
          <tr>
            <th>Name</th>
            <th>Dachart</th>
            <th>Preis</th>
            <th>kWp</th>
            <th>Speicher</th>
            <th>Wallbox</th>
            <th>Status</th>
            <th>Aktionen</th>
          </tr>
        </thead>
        <!--Einfügen der Customer Row Component-->

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

  .admin-header {
    display:flex;
    flex-direction: row;
    flex-wrap:nowrap;
    justify-content:space-between;
    
  }

 

</style>
