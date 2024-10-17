<template>
    <div class="search-bar">
        <button class="search-icon">
        </button>
        <input type="text" placeholder="Nach Kunden suchen..." /> 
    </div>
    
</template>


<style scoped>
 .search-bar{
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    position: relative;
    height: 48px;
    width: 344px;
    margin-bottom: 0px;
    border-width: 1px;
    border-radius: 500px;
    background-color: #fff;
    border: 1px solid #EDEDED;
    margin-top:30px;
    /* font-family: 'Poppins', sans-serif; */
    line-height: 25.5px;
    text-align: center;
    margin-left:80px;
    margin-right:-60px;
    align-items: center;
    box-sizing: border-box;
    padding-right: 10px;
    padding-left: 5px;
    box-sizing: border-box;
}

.search-bar::placeholder {
    font-weight: 500;
    
    
}

input{
    flex-grow: 1;
    position: relative;
    margin-bottom: 0px;
    border: none;
    /* font-family: 'Poppins', sans-serif; */
    line-height: 25.5px;
    padding-left: 15px;
    margin-top:4px;
    box-sizing: border-box; /* Prevent input from overflowing the container */
    outline:none;
}

input::placeholder{
    color: #212529;
    font-size: 17px;
    font-weight: 500;
    opacity:50%;

}

input:focus {
  border: none; /* Remove border on focus */
  outline: none; /* Remove focus outline */
}

.search-icon{
    height: 20px; /* Adjust height if needed */
    width: 20px; /* Adjust width if needed */
    margin-left:20px;
    
    background-size: contain; /* Make sure the background fits */
    border: 0; /* Remove border */
    opacity: 100%; /* Set opacity */
    cursor: pointer; /* Change cursor to pointer on hover */
    background:url('@/assets/Vector (1).svg');
}
</style>