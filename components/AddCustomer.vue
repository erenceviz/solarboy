<template>
    <button @click="addCustomer" class="add-customer">Neuen Kunden anlegen</button>
</template>

<script setup>
    const addCustomer = () =>{
        // TODO
    }
</script>

<style scoped>
 .add-customer{
    height: 52px;
    width: 281px;
    border-width :1px;
    border-radius: 500px;
    border-color: #EDEDED;
    border: 1px solid #EDEDED;
    color: #212529;
    /* font-family: 'Poppins', sans-serif; */
    font-size:17px;
    font-weight: 500 !important;
    line-height: 25.5px;
    margin-top:30px;
    margin-right: 40px;
    margin-left:-100px;
    box-shadow: 0px 1px 2px 0px #00000005;

    box-shadow: 0px 4px 4px 0px #00000005;

    box-shadow: 0px 9px 6px 0px #00000003;

    box-shadow: 0px 16px 7px 0px #00000000;

    box-shadow: 0px 26px 7px 0px #00000000;
    
    padding: 13px 25px 13px 25px;
  }
</style>