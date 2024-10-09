<template>
    <div>
      <div class="admin-header">
        <!-- Admin Panel Header erste Reihe-->

        <p class="customerlist">Ebene 2</p>
        <input type="text" placeholder="Nach Kunden suchen..." class="search-bar"/>
        <!-- Filterbutton -->
        <div class="filter-status">
          <button @click="toggleFilterOptions">O</button>
          <button @click="clearFilterOptions">X</button>
          <div v-if="filterVisible" class="filter-options">
            <ul>
              <li>
                <input type="checkbox" v-model="filters.Deal" id="filter-deal" />
                <label for="filter-deal">Deal</label>
              </li>
              <li>
                <input type="checkbox" v-model="filters.Offen" id="filter-offen" />
                <label for="filter-offen">Offen</label>
              </li>
              <li>
                <input type="checkbox" v-model="filters['1.Termin']" id="filter-termin" />
                <label for="filter-termin">1.Termin</label>
              </li>
              <li>
                <input type="checkbox" v-model="filters.Folgetermin" id="filter-folgetermin" />
                <label for="filter-folgetermin">Folgetermin</label>
              </li>
              <li>
                <input type="checkbox" v-model="filters['No Deal']" id="filter-nodeal" />
                <label for="filter-nodeal">NoDeal</label>
              </li>
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

  //Filter initial auf falsch gestellt
  const filters = ref({
    Deal: false,
    Offen: false,
    '1.Termin': false,
    Folgetermin: false,
    'No Deal': false,
  });


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
    position:relative;
    
  }

  .search-bar{
    height: 52px;
    width: 350px;
    border-width: 1px;
    border-radius: 500px;
    border-color: #EDEDED;
    border: 1px solid #EDEDED;
    /* border-color: #000000; */
    margin-top:40px;
    font-size:17px;
    font-weight: 500 !important;
  }

  .add-customer{
    height: 52px;
    width: 281px;
    color: #F6F7F8;
    border-width :1px;
    border-radius: 500px;
    border-color: #EDEDED;
    border: 1px solid #EDEDED;
    color: #212529;
    font-size:17px;
    font-weight: 500 !important;
    margin-top:40px;
    box-shadow: 0px 1px 2px 0px #00000005;

    box-shadow: 0px 4px 4px 0px #00000005;

    box-shadow: 0px 9px 6px 0px #00000003;

    box-shadow: 0px 16px 7px 0px #00000000;

    box-shadow: 0px 26px 7px 0px #00000000;
   

  }
  
  
  .filter-status{
    position:relative;
    width:319px;
    margin-top:40px;
  }

  .filter-options{
    position:absolute;
    border-radius: 15px;
    border: 1px solid #ccc;
    padding: 10px;
    width:240px;
    display:flex;
    flex-wrap:nowrap;
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

</style>
