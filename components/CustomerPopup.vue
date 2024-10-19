<template>
    <!-- Full-page overlay -->
    <div v-if="isVisible" class="popup-overlay" @click="closePopup">
      <!-- Centered popup content -->
      <div class="popup-content" @click.stop>
        <div class="popup-header">
            <div class="edit-header">
                <p>{{ title }}</p>
                <span>Fülle die Input-Felder aus, um einen neuen Kunden anzulegen</span>
            </div>
            
            <span class="close-btn" @click="closePopup"></span>
        </div>

        <!--erste Reihe des Forms-->
        <div class="edit-row1">
            <div class="edit-name">
                <span>Vorname</span>
                <input class="input-name" placeholder="Vorname"/>
            </div>
            
            <div class="edit-name">
                <span>Nachname</span>
                <input class="input-name" placeholder="Nachname"/>
            </div>
            
            <div class="edit-name">
                <span>WhatsApp</span>
                <input class="input-name" placeholder="Nummer"/>
            </div>
        </div>

        <!--zweite Reihe des Forms-->
        <div class="edit-row2">
            <div class="edit-payment">
                <span>Dach Komplexität</span>
                <div class="zahlung-container">
                    <input type="text" class="input-name" placeholder="Zahlungsart auswählen" readonly @click="togglePaymentOptions" />
                    <button @click="togglePaymentOptions" :class="{ 'rotated': isRotated }" class="toggle-payments"></button>
                </div>
                
                <transition name="slide-fade" mode="out-in">
                    <div v-if="zahlungVisible" :class="['payment-options', { 'visible': zahlungVisible }]">
                        <ul>
                            <li>Barzahlung</li>
                            <li>Finanzierung</li>
                        </ul>
                    </div>
                </transition>
            </div>
            
            <div class="edit-name">
                <span>Adresse</span>
                <div class="edit-adresse-row1">
                    <input class="input-strasse" placeholder="Straße"/>
                    <input class="input-hausnr" placeholder="Hausnr."/>
                </div>
                <div class="edit-adresse-row2">
                    <input class="input-plz" placeholder="PLZ"/>
                    <input class="input-ort" placeholder="Ort"/>
                </div>
            </div>
            
            <div class="edit-name">
                <span>Gerüst</span>
                <input class="input-name" placeholder="Gerüst"/>
            </div>
        </div>

        <!--dritte Reihe des Forms-->
        <div class="edit-row3">
            <div class="edit-name">
                <span>Dach Komplexität</span>
                
                    <input class="input-dachart" placeholder="Dachart auswählen"/>
               
            </div>
            
            <div class="edit-name">
                <span>Dachart</span>
                <div class="edit-adresse-row1">
                    <input class="input-dachart" placeholder="Dachart auswählen"/>
                </div>
            </div>
            
            <div class="edit-name">
                <span>2. WR</span>
                <input class="input-name" placeholder="Gerüst"/>
            </div>
        </div>

        <!--vierte Reihe des Forms-->
        <div class="edit-row3">
            <div class="edit-name">
                <span>Spezifischer Ertrag</span>
                <input class="input-name" placeholder="Wert zwischen 600-1100 eingeben..."/>
            </div>
            
            <div class="edit-name">
                <span>Anfahrt</span>
                <div class="edit-adresse-row1">
                    <input class="input-name" placeholder="Zeit in Minuten eingeben..."/>
                </div>
            </div>
            
            <div class="edit-name">
                <span>Zähler</span>
                <input class="input-name" placeholder="Zähler auswählen..."/>
            </div>
        </div>
        
        <!-- Reihe für Buttons -->
        <div class="button-row">
            <button type="button" @click="closePopup" class="cancel-btn">Abbrechen</button>
            <button type="submit" class="submit-btn">Anlegen</button>
        </div>
        <form @submit.prevent="handleSubmit">
          
        </form>
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  

  const zahlungVisible = ref(false);
  const isRotated = ref(false);

  const props = defineProps({
    isVisible: Boolean,
    title: {
      type: String,
      default: 'Add/Edit Customer'
    }
  });

  const togglePaymentOptions = () => {
    isRotated.value = !isRotated.value;
    zahlungVisible.value = !zahlungVisible.value;
};
  
  const emit = defineEmits(['close', 'save']);
  const formData = ref({ name: '', email: '', phone: '' });
  
  const closePopup = () => {
    emit('close');
  };
  
  const handleSubmit = () => {
    emit('save', formData.value);
    closePopup();
  };
  </script>
  
  <style scoped>
  /* Full-page overlay */

  .popup-header{
    display:flex;
    justify-content: space-between;
    flex-direction: row;
    flex-wrap: nowrap;
    align-items: center;
    width:1166px;
    height:70px;
    margin-top:0px;
    
  }

  .edit-header{
    margin-top:0px;
  }

  .edit-header span{
    font-size:17px;
    opacity: 50%;
    font-weight: 500;
  }

  .edit-row1{
    display:flex;
    justify-content: space-between;
    flex-direction: row;
    margin-top:40px;
    gap:30px;
    height:86px;
    text-align: center;
  }

  .edit-row1 span{
    width: 368px;
    height:26px;
    opacity: 0px;
    text-align: left;
    font-size:17px;
    font-weight:500;
    margin-bottom:10px;
    max-width: 368px;
  }

  .edit-name{
    width: 368px;
    max-width: 368px;
    display:flex;
    flex-direction: column;
    gap:0px;
    height: 86px;
  }

  .input-name{
    background-color: #fff;
    border: 1px solid #EDEDED;
    border-radius: 500px;
    height:50px;
    margin-bottom:0px;
    padding-left: 20px;
    width: 348px;
    max-width: 368px;
  }

  input::placeholder{
    font-size: 14px;
    font-weight: 300;
    opacity:50%;
  }

  .edit-row2{
    display:flex;
    justify-content: space-between;
    flex-direction: row;
    margin-top:40px;
    gap:30px;
    height:156px;
    text-align: center;
  }

  .edit-row2 span{
    width: 368px;
    height:26px;
    opacity: 0px;
    text-align: left;
    font-size:17px;
    font-weight:500;
    margin-bottom:10px;
    max-width: 368px;
  }

  .input-strasse{
    background-color: #fff;
    border: 1px solid #EDEDED;
    border-radius: 500px;
    height:50px;
    margin-bottom:0px;
    padding-left: 20px;
    width: 234px;
    
  }

  .input-hausnr{
    background-color: #fff;
    border: 1px solid #EDEDED;
    border-radius: 500px;
    height:50px;
    margin-bottom:0px;
    padding-left: 20px;
    width:76px;
    
  }
  
  .edit-adresse-row1{
    display:flex;
    justify-content: space-between;
    flex-direction: row;
  }

  .edit-adresse-row2{
    display:flex;
    justify-content: space-between;
    flex-direction: row;
    margin-top:20px;
  }

  .input-plz{
    background-color: #fff;
    border: 1px solid #EDEDED;
    border-radius: 500px;
    height:50px;
    margin-bottom:0px;
    padding-left: 20px;
    width:76px;
    
  }

  .input-ort{
    background-color: #fff;
    border: 1px solid #EDEDED;
    border-radius: 500px;
    height:50px;
    margin-bottom:0px;
    padding-left: 20px;
    width: 234px;
    
  }

  .edit-row3{
    display:flex;
    justify-content: space-between;
    flex-direction: row;
    margin-top:40px;
    gap:30px;
    height:86px;
    text-align: center;
  }

  .edit-row3 span{
    width: 368px;
    height:26px;
    opacity: 0px;
    text-align: left;
    font-size:17px;
    font-weight:500;
    margin-bottom:10px;
    max-width: 368px;
  }

  .input-dachart{
    background-color: #fff;
    border: 1px solid #EDEDED;
    border-radius: 500px;
    height:50px;
    margin-bottom:0px;
    padding-left: 20px;
    width: 348px;
    max-width: 368px;
  }

  .button-row{
    display:flex;
    justify-content: space-between;
    margin-top:80px;
    width:1166px;
  }

  .zahlung-container{
    position: relative; /* Position relative to position the button */
    width: 368px; /* Match the width of other input fields */
  }

  .toggle-payments {
    position: absolute; /* Position button absolutely within the input container */
    right: 20px; /* Position it within the padding */
    top: 50%; /* Center it vertically */
    transform: translateY(-50%); /* Adjust vertical alignment */
    background: url('@/assets/01 align center down.svg') no-repeat center center; /* Change to your button image */
    background-size: contain; /* Ensure the image scales correctly */
    background-position: center;
    width: 20px; /* Set button size */
    height: 20px; /* Set button size */
    border: none; /* Remove default button styling */
    cursor: pointer; /* Change cursor to pointer */
    opacity: 100%; /* Ensure visibility */
    transition: transform 0.3s ease;
    transform-origin: center;
    
}

.toggle-payments.rotated {
    transform: translateY(-50%) rotate(180deg); /* Rotate when active */
}

.payment-options{
    
    width: 368px;
    height: 74px;
    gap: 10px;
    border-radius: 15px;
    border: 1px 0px 0px 0px;
    margin-top:10px;
    z-index: 9999;
    background-color: rgba(255, 255, 255, 1);
    border: 1px solid #EDEDED;
    display: flex;
    justify-content: space-between;
    flex-direction: column;
    padding-top:20px;
    padding-bottom:0px;
    padding-left:20px;
    align-items: center;

}

.payment-options{
    width: 368px;
    height: 104px;
    gap: 10px;
    border-radius: 15px;
    border: 1px 0px 0px 0px;
    margin-top:10px;
    z-index: 9999;
    background-color: rgba(255, 255, 255, 1);
    border: 1px solid #EDEDED;
    display: flex;
    justify-content: space-between;
    flex-direction: column;
    padding-left:0px;
}

.payment-options ul {
        list-style-type: none; /* Removes bullet points */
        padding: 0;  
        width:100%;
        margin-top:0;
        margin-bottom: 0;
        height:100%;
        overflow-y: hidden;
  }

  .payment-options li {
        margin-bottom: 20px;    
        display:flex;
        flex-wrap:nowrap;
        align-items: start;
        padding: 0px 15px 0px 15px;
    }

    .payment-options li:hover{
        background-color: #F6F7F8;
        max-width:330px;
        height:41px;
        border-radius: 13px;
        padding: 0px 0px 0px 10px;
        align-items: center;
    }

.edit-payment{
    width: 368px;
    max-width: 368px;
    display:flex;
    flex-direction: column;
    gap:0px;
    height: 210px;
  }

  .cancel-btn{
    width:575.5px;
    height:54px;
    border-radius: 10px;
    background-color: #ECECEC;
    border: 1px solid #F8F8F8;
    color:#212529;
    font-size:17px;
    font-weight: 500;
  }

  .submit-btn{
    width:575.5px;
    height:54px;
    border-radius: 10px;
    background-color: #2A3F94;
    border: 1px solid #F8F8F8;
    color:#fff;
    font-size:17px;
    font-weight: 500;
  }


  p{
    font-size: 26px;
    font-weight: 500;
    color: #212529;
    margin-bottom:5px;
    margin-top:0px;

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
    z-index: 1000; /* High z-index to ensure it appears above other content */
  }
  
  /* Popup content centered on the screen with specific dimensions */
  .popup-content {
    background-color: white;
    padding: 25px 30px 25px 30px;
    display:flex;
    flex-direction: column;
    align-items: center;
    border-radius: 10px;
    width: 1196px; /* Set width to 1226 pixels */
    height: 783px; /* Set height to 808 pixels */
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    z-index: 1001; /* Ensure content is on top of overlay */
    position: relative; /* Ensure the close button is within the popup */
  }
  
  /* Close button */
  .close-btn {
    cursor: pointer;
    background: url('@/assets/cross-small 1.svg') no-repeat center center; /* Center the image */
    background-size: contain; /* Ensure the image scales within the button */
    width: 20px; /* Width of the button */
    height: 20px; /* Height of the button */
    margin-bottom:30px;
    opacity: 1;
    z-index: 99999;
    }
  </style>
  