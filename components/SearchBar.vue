<template>
    <input type="text" placeholder="Nach Kunden suchen..." class="search-bar"/>
</template>


<style scoped>
 .search-bar{
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
    margin-left:100px;
    margin-right:-70px;
}

.search-bar::placeholder {
    font-weight: 500;
    
    
}

input::placeholder{
    color: #212529;
    font-size: 17px;
    font-weight: 500;
    opacity:50%;
}
</style>