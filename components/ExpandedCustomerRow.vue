<template>
    <tr class="expanded-row" :style="{ backgroundColor: backgroundColor }">
        <td>
            <span>Adresse</span>
            <p style="width:190px; margin-top:5px; margin-bottom:0px;">Hauptstraße 102b, 04328 Leipzip</p>
        </td>
        <td>
            <span>WhatsApp</span>
            <p>+01235678234</p>
        </td>
        <td>
            <span>Dach Kompl.</span>
            <p>LULE</p>
        </td>
        <td>
            <span>Gerüst</span>
            <p>LULE</p>
        </td>
        <td>
            <span>2. WR</span>
            <p>ICON</p>
        </td>
        <td>
            <span>Spez. Ertrag</span>
            <p>900</p>
        </td>
        <td>
            <span>2. WR</span>
            <p>ICON</p>
        </td> 
        <td>
            <span>Anfahrt</span>
            <p>30min</p>
        </td>
        <td>
            <span>Zähler</span>
            <p>SLS oder AC</p>
        </td>
    </tr>

</template>


<script setup>
const props = defineProps({
  customer: {
    type: Object,
    required: true,
  },
  backgroundColor: {
    type: String,
    default: '#FFFFFF', // Fallback color
  },
  index: {
    type: Number,
    required: true,
  },
});

const computedBackgroundColor = computed(() => {
  // Check if the current index is even or odd
  const isEven = index % 2 === 0;
  
  // Return the appropriate background color
  return isEven ? backgroundColor : '#F0F0F0'; // Replace with your desired alternate color
});
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600;700&display=swap');


div, input, button {
  font-family: 'Poppins', sans-serif;
}



.expanded-row {
  transition: all 0.3s ease-in-out;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  padding: 0px 40px 10px 50px;
  align-items: center;
  max-width: 1366px;
  margin-left: -10px;
}

.expanded-row span {
  font-size: 17px;
  font-weight: 50;
  opacity: 50%;
}




</style>