<template>
    <div>
      <div class="admin-header">
        <!-- Admin Panel Header erste Reihe-->

        <h1>Admin Panel</h1>
        <input type="text" placeholder="Nach Kunden suchen..." class="search-bar"/>
        <!-- Filterbutton -->
        <div class="filter-status">
          <button @click="toggleFilterOptions">O</button>
          <button @click="clearFilterOptions">X</button>
          <div v-if="filterVisible" class="filter-options">
            <ul>
              <li @click="applyFilter('Deal')">Deal</li>
              <li @click="applyFilter('Offen')">Offen</li>
              <li @click="applyFilter('1.Termin')">1.Termin</li>
              <li @click="applyFilter('Folgetermin')">Folgetermin</li>
              <li @click="applyFilter('No Deal')">No Deal</li>
            </ul>
          </div>
        </div>
        <button @click="addCustomer" class="add-customer">Neuen Kunden anlegen</button>
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
  
  // Testkunde
  const customers = ref([
  { id: 1, name: 'John Doe', dachart: 'Flachdach', preis: '15,000 €', kWp: 8, speicher: 'Ja', wallbox: 'Nein', status: 'Deal' }
  ]);


  const addCustomer = () =>{
    // TODO
  }

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

  const filterVisible = ref(false);

  const toggleFilterOptions = () => {
    filterVisible.value = !filterVisible.value;
  };

  const clearFilters = () => {
    // TODO
  };

  const applyFilter = (filter) => {
    // TODO
    console.log(`Applied filter: ${filter}`);
  };
</script>



<style scoped>
  
</style>
  