<script setup>
import FooterimageComponent from './FooterimageComponent.vue';
import pin from '../assets/pin.png';
import url from '../assets/url.png';
import twitter from '../assets/twitter.png';
import office from '../assets/office-building.png'; 
import {ref} from 'vue'

const searchData = ref(null)

import axios from 'axios'

const response =  axios.get(`https://api.github.com/users/${searchUser.value}`);
    searchData.value = response.data;
</script>

<template>
<div class="details">
    <div class="detail1">
<FooterimageComponent class="cardItem1" :images="pin" cardtext="searchData.location"/>
<FooterimageComponent class="cardItem2" :images="url" cardtext="https://github.blog"/>
</div>
<div class="detail2">
<FooterimageComponent class="cardItem3" :images="twitter" cardtext="Not Available"/>
<FooterimageComponent class="cardItem4" :images="office" cardtext="@github"/>
</div>
</div>
</template>

<style scoped>
.details{
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    gap: 10px;
    padding-top: 34px 200px 40px 200px;
}
.detail1{
    display: flex;
    flex-direction: column;
    gap:20px ;
}

.detail2{
    display: flex;
    flex-direction: column;
    gap:20px ;
}






</style>