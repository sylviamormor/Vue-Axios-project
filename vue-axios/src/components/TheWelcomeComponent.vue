<script setup>
import axios from 'axios'
import { ref } from 'vue';
import NavbarComponent from './NavbarComponent.vue';
import SearchComponent from './SearchComponent.vue';


const searchUser = ref("")
const searchData = ref(null)
const errorMessage = ref("")

async function searchUserInfo() {
    try {
        const response = await axios.get(`https://api.github.com/users/${searchUser.value}`);
        searchData.value = response.data;
        console.log(response);
    } catch (error) {
        console.error(error);
        errorMessage.value = 'No results';
        searchData.value = null;
    }
    searchUser.value = ""
}

</script>

<template>
    <NavbarComponent />
    <div class="content">
        <SearchbarComponent>
            <div class="inputIcons">
                <input class="inputArea" type="text" v-model="searchUser" placeholder="Search GitHub username…">
           
            <button @click.prevent="searchUserInfo" class="btn">Search</button>
        </div>
        </SearchbarComponent> 
        <div class="bio">    
            <div class="pic">
                <img class="profilepic" :src="searchData?.avatar_url" alt="">
            </div>
            <div class="bioname">
                <div>
                    <h1 class="namedetails">{{ searchData?.name }}</h1>
                    <p class="handle">{{ searchData?.login }}</p>
                </div>
                <div class="div">
                    <p class="joined">{{ searchData?.created_at }}</p>
                </div>
            </div>
            <div class="biodetails">
                <p v-if="searchData?.bio">{{ searchData?.bio   }}</p>
                <p v-else>This profile has no bio</p>
            </div>
            <div class="counters">
                <div class="repos">
                    <p class="title">Repos</p>
                    <p class="count">{{ searchData?.public_repos }}</p>
                </div>
                <div class="repos">
                    <p class="title">Followers</p>
                    <p class="count">{{ searchData?.followers }}</p>
                </div>
                <div class="repos">
                    <p class="title">Following</p>
                    <p class="count">{{ searchData?.following }}</p>
                </div>
            </div>
            <div class="social">
                <p  v-if="searchData?.location"><i class="fa fa-map-marker fa-2x"></i> {{ searchData?.location }}</p>
                <p v-else> Not Available</p>
                <p v-if="searchData?.blog"></p>
                    <p v-else>
                        <img src="../assets/url.png" alt=""> 
                        <p>Not Available</p>
                    {{ searchData?.blog }}
                </p>
                <p v-if="searchData?.twitter_searchUser">
                    <i class="fa fa-twitter fa-2x"></i> {{ searchData?.twitter_searchUser }}</p>
                <p v-else> Not Available</p>
                <p v-if="searchData?.company">
                    <img src="../assets/office-building.png" alt="">
                    {{ searchData?.company }}
                </p>
                <p v-else> Not Available</p>
            </div>
            
        </div>
    </div>
</template>

<style scoped>
    .btn {
        width: 84px; 
        padding: 13px 16px;
        border-radius: 10px;
        background: #0079FF;
        border: none;
        color: #fff;
    }
    


.inputIcons {
    width: 100%;
    margin-bottom: 10px;
    display: flex;
    border-radius: 15px;
    background: #1E2A47;
}

.icon {
    padding: 12px;
    color: #0079FF;
    min-width: 50px;
    height: 20px;
    text-align: center;
    margin-top: 11px;
}

.inputArea {
    width: 100%;
    margin-top: 10px;
    padding: 10px 5px 10px 40px;
    text-align: center;
    background-color: transparent;
    border: none;
    /* color: #FFF; */
    font-size: 13px;
    font-weight: 400;
    line-height: 25px;
    text-align: start;
    gap: 5px;
    }

    .content{
        margin: 35px 0 14px 0;
        display: flex;
        flex-direction: column;
        gap: 20px;
        border-radius: 15px;
    }
    .bio{
        display: grid !important;
        border-radius: 15px;
        background: #1E2A47;
        gap: 20px 20px;
        padding: 7% 5%;
    }
    .pic{
        grid-column: 1 / 2;
    }
    .profilepic{
        width: 70px;
        height: 70px;
        border-radius: 70px;
background: url(<path-to-image>), lightgray 50% / cover no-repeat;
    }
    .bioname{
        grid-column: 2 / 12;
    }
    .namedetails{
        color: #FFF;
        font-size: 16px;
        font-weight: 700;
    }
    .handle{
        color: #0079FF;
        font-size: 13px;
        font-weight: 400;
    }
    .joined{
        color: #FFF;
        font-size: 13px;
        font-weight: 400;
    }
    .biodetails{
        grid-column: 1 / 12;
        color: #FFF;
        font-size: 13px;
        font-weight: 400;
        line-height: 25px;
    }
    .counters{
        grid-column: 1 / 12;
        padding: 15px 32px;
        display: flex;
        justify-content: space-between;
        border-radius: 10px;
        background: #141D2F;
    }
    .repos{
        display: flex;
        flex-direction: column;
        gap: 10px;
    }
    .repos .title{
        color: #FFF;
        text-align: center;
        font-size: 11px;
        font-weight: 400;
    }
    .repos .count{
        color: #FFF;
        font-size: 16px;
        font-weight: 700;
    }
    .social{
        grid-column: 1 / 12;
        display: grid;
        grid-template-columns: 1fr;
        gap: 10px;
    }
    .social p{
        color: #FFF;
        font-size: 13px;
        font-weight: 400;
        display: flex;
        align-items: center;
        gap: 15px;

    }
    @media (min-width: 490px){
        .social{
            grid-template-columns: repeat(2, 1fr);
        }
        .profilepic{
        width: 117px;
        height: 117px;
        }
        .namedetails{
            font-size: 26px;
        }
        .handle{
            font-size: 16px;
        }
        .joined{
            font-size: 15px;
        }
        .biodetails{
            font-size: 15px;
        }
        .repos .title{
            font-size: 13px;
        }
        .repos .count{
            font-size: 22px;
        }
    }
    @media (min-width: 768px){
        .social{
            grid-template-columns: repeat(2, 1fr);
        }
        .profilepic{
        width: 117px;
        height: 117px;
        }
        .namedetails{
            font-size: 26px;
        }
        .handle{
            font-size: 16px;
        }
        .joined{
            font-size: 15px;
        }
        .biodetails{
            grid-column: 2 / 12;
            font-size: 15px;
        }
        .counters{
            grid-column: 2 / 12;
        }
        .bioname{
            display: flex;
            justify-content: space-between;
        }
        .biodetails{
            font-size: 15px;
        }
        .repos .title{
            font-size: 13px;
        }
        .repos .count{
            font-size: 22px;
        }
        .social{
            grid-column: 2 / 12;
            grid-template-columns: repeat(2, 1fr);
        }
    }

</style>























    
   





















 -->
