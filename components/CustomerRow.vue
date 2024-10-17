<!-- CustomerRow als Component für die Tabelle-->

<template>
    <tr>
        <td>{{ customer.name }}</td>
        <td>{{ customer.dachart }}</td>
        <td>{{ customer.preis }}</td>
        <td>{{ customer.kWp }}</td>
        <td>{{ customer.speicher }}</td>
        <td>{{ customer.wallbox }}</td>
        <td>{{ customer.status }}</td>
        <td>
            <button @click="$emit('edit', customer)">Edit</button>
            <button @click="$emit('clone', customer)">Clone</button>
            <button @click="$emit('delete', customer)">Delete</button>
        </td>
    </tr>
</template>

<script setup>
import { defineProps } from 'vue';

const props = defineProps({
  customer: {
    type: Object,
    required: true,
  },
});
</script>



<style scoped>

</style>