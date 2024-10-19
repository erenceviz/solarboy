<template>
    <div class="add-customer">
        <button class="add-button"></button>
        <button @click="addCustomer" class="new-customer">Neuen Kunden anlegen</button>
    </div>
    <!-- Customer Popup -->
    <CustomerPopup
          :isVisible="isPopupVisible"
          title="Neuen Kunden anlegen"
          @close="closePopup"
          @save="saveCustomer"
        />
</template>

<script setup>
import { ref } from 'vue';
import CustomerPopup from './CustomerPopup.vue';
const isPopupVisible = ref(false);

const addCustomer = () => {
  isPopupVisible.value = true;
};

const closePopup = () => {
  isPopupVisible.value = false;
};

// Save customer details
const saveCustomer = (customerData) => {
  console.log('Customer saved:', customerData);
  // Add logic to save the customer
};


</script>

<style scoped>
 .add-customer {
  display: flex;
  justify-content: center; /* Center content horizontally */
  align-items: center; /* Center content vertically */
  flex-direction: row;
  max-height: 52px;
  max-width: 281px;
  width:100%;
  border-radius: 500px;
  border: 1px solid #EDEDED;
  background-color: #F6F7F8;
  margin-top: 30px;
  margin-right: 40px;
  margin-left: -100px;
  padding: 13px 25px;
  box-sizing: border-box;

  /* Simplified box-shadow */
  box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.05); /* You can adjust this for a softer effect */
}

.add-button {
  height: 20px; /* Set the desired height */
  width: 20px;  /* Set the desired width */
  background-size: contain; /* Ensures the image scales within the button */
  background-position: center; /* Center the image */
  background-repeat: no-repeat; /* Prevent image repeat */
  background-color: #F6F7F8;
  border: 0; /* Remove border */
  cursor: pointer; /* Change cursor to pointer on hover */
  margin-right: 5px; /* Space between icon and button text */
  background-image: url('@/assets/user-add 1.svg'); /* Background image */
  padding: 0; /* Ensure no padding */
}


.new-customer {
  border: none; /* Remove border on the button */
  background: none; /* Remove background for a cleaner look */
  color: #212529;
  font-size: 17px;
  font-weight: 500;
  text-align: center;
  padding: 0; /* Remove padding to make sure it aligns properly */
}

</style>