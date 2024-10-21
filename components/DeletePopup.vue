<template>
    <div v-if="isVisible" @click="closePopup" class="popup-overlay">
      <div class="popup-content" @click.stop> <!-- Prevent overlay click from closing the popup -->
        <div class="popup-header">
            <div class="edit-header">
                <p>{{ title }}</p>
                <span> Möchtest du den Kunden Zachy Kurt wirklich löschen?</span>
            </div>
            
            <span class="close-btn" @click="closePopup"></span>
        </div>
        
        <div class="popup-actions">
          <button @click="closePopup" class="cancel-button">Abbrechen</button>
          <button @click="confirmDelete" class="confirm-button">Bestätigen</button>
        </div>
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref, defineProps } from 'vue';
  
  // Define props for visibility and title
  const props = defineProps({
    isVisible: {
      type: Boolean,
      required: true,
    },
    title: {
      type: String,
      required: true,
    },
  });

  const emit = defineEmits(['close', 'delete']);
  
  // Method to close the popup
  const closePopup = () => {
    emit('close');
  };
  
  // Method to confirm deletion
  const confirmDelete = () => {
    //emit('delete');
  };
  </script>
  
  <style scoped>

@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600;700&display=swap');


div, input, button,span {
  font-family: 'Poppins', sans-serif;
}
  .popup-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    background-color: #00000099; /* Semi-transparent black background */
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 9999;
  }
  
  .popup-content {
    background-color: white;
    padding: 25px 30px 25px 30px;
    height:164px;
    width:600px;
    display: flex;
    flex-direction: column;
    align-items: center;
    border-radius: 10px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    z-index: 1001;
    position: relative;
  }
  
  .popup-actions {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    width:600px;
    height:54px;
    gap: 10px;
    margin-top: 40px;
  }

  p{
    font-size: 26px;
    font-weight: 500;
    color: #212529;
    margin-bottom:5px;
    margin-top:0px;

  }

  .popup-header{
    display:flex;
    justify-content: space-between;
    flex-direction: row;
    flex-wrap: nowrap;
    align-items: center;
    width:600px;
    height:70px;
    margin-top:0px;
    
  }
  
  .confirm-button {
    background: #C93C2D;
    border: 1px solid #F8F8F8;
    width: 292.5px;
    height: 54px;
    padding: 14px 100.5px 14px 100px;
    gap: 0px;
    border-radius: 10px;
    color:white;
    opacity: 0px;
    cursor: pointer;
    font-size:17px;
    font-weight:500;
  }
  
  .cancel-button {
    background: #ECECEC;
    border: 1px solid #F8F8F8;
    width: 292.5px;
    height: 54px;
    padding: 14px 100.5px 14px 100px;
    gap: 0px;
    border-radius: 10px;
    color:#212529;
    opacity: 0px;
    cursor: pointer;
    font-size:17px;
    font-weight:500;
  }

  .close-btn {
    cursor: pointer;
    background: url('@/assets/cross-small 1.svg') no-repeat center center; /* Center the image */
    background-size: contain; /* Ensure the image scales within the button */
    width: 20px; /* Width of the button */
    height: 20px; /* Height of the button */
    margin-bottom:40px;
    opacity: 1;
    z-index: 99999;
    }

    .edit-header{
    margin-top:0px;
  }

  .edit-header span{
    font-size:17px;
    opacity: 50%;
    font-weight: 500;
  }
  </style>
  