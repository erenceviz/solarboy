<template>
    <div class="table-container" >
        <table>
           <thead>
             <tr class="table-head">
               <th style="margin-right: 80px;">Name</th>
               <th>Dachart</th>
               <th>Preis</th>
               <th>kWp</th>
               <th>Speicher</th>
               <th>Wallbox</th>
               <th>Status</th>
               <th>Aktionen</th>
             </tr>
           </thead>
         </table>

    </div>
</template>



<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600;700&display=swap');


div, input, button,span {
  font-family: 'Poppins', sans-serif;
}

 .table-head{
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
    padding: 5px; /* Adjust the padding to reduce the space */
    text-align: center; /* Centers the text inside each cell */
    font-weight: 500;
}

  thead {
    text-align: center;
  }

    .table-head th {
        width: 150px; /* Set a fixed width for the other columns */
    }

  .table-head th:nth-child(8){
      padding-right:40px; /* Adjust this width to control the size */
  }

  table {
    width: 100%; /* Adjusts the width of the table, can be changed as needed */
    width:1366px;
    border-collapse: collapse; /* Ensures the table cells share borders */
    z-index: 1;
    position: relative;
  }

  .table-container {
    position: relative;
    display: flex;
    flex-direction: column;
    justify-content: center; /* Centers the table horizontally */
    width: 1366px;
    width: 100%; /* Ensures the container spans the entire width of the page */
    font-size: 17px;
    font-weight: 400;
    opacity: 50%;
    margin-top:10px;
    z-index: 1;
    overflow: visible;
    
  }

  .table-container table {
    align-self: flex-start; /* Ensure the table aligns to the start */
    width: 100%; /* Adjusts the width of the table */
    border-collapse: collapse; /* Ensures the table cells share borders */
    position: relative;
    border-radius: 30px 30px 0 0; /* Top-left and top-right corners */
    overflow: hidden; /* Ensures the corners are clipped */
    margin-left:-10px;
}


 
  .table-container table {
      border: 1px solid #EDEDED; /* Adjust the color as needed */
  }

</style>