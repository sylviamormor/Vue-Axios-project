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
    <NavbarComponent/>
    <div class="content">
        <SearchComponent>
            <div class="input-icons">
                <i class="fa fa-search icon"></i>
                <input class="input-field" type="text" v-model="searchUser" placeholder="Search GitHub username…">
            </div>
            <button @click.prevent="searchUserInfo" class="btn">Search</button>
        </SearchComponent> 
   <div class="profile">
        <div class="image">
            <img class="profileImage" :src="searchData?.avatar_url" alt="">
        </div>
        <div class="userDetails">
            <div>
                <h1 class="userName">{{ searchData?.name }}</h1>
                <p class="page">{{ searchData?.login }}</p>
            </div>
            <div class="date">
                <p class="dateJoined">{{ searchData?.created_at }}</p>
            </div>
        </div>
        <div class="profileDetails">
            <p v-if="searchData?.bio">{{ searchData?.bio }}</p>
            <p v-else>This profile has no bio</p>
        </div>
        <div class="dataList">
            <div class="repos">
                <p class="data">Repos</p>
                <p class="number">{{ searchData?.public_repos }}</p>
            </div>
            <div class="repos">
                <p class="data">Followers</p>
                <p class="number">{{ searchData?.followers }}</p>
            </div>
            <div class="repos">
                <p class="data">Following</p>
                <p class="number">{{ searchData?.following }}</p>
            </div>
        </div>
        <div class="footer">
            <p v-if="searchData?.location"><i class="fa fa-map-marker fa-2x"></i> {{ searchData?.location }}</p>
            <p v-else> Not Available</p>
            <p v-if="searchData?.blog">
                <!-- <i class="fa fa-link"></i>  -->
                <img src="../assets/url.png" alt="">
                {{ searchData?.blog }}
            </p>
            <p v-if="searchData?.twitter_searchUser"><i class="fa fa-twitter fa-2x"></i> {{ searchData?.twitter_searchUser
            }}</p>
            <p v-else> Not Available</p>
            <p v-if="searchData?.company">
                <!-- <i class="fa fa-github"></i>  -->
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
    
.input-icons i {
    position: absolute;
}

.input-icons {
    width: 100%;
    margin-bottom: 10px;
}

.icon {
    padding: 12px;
    color: #0079FF;
    min-width: 50px;
    height: 20px;
    text-align: center;
    margin-top: 11px;
}

/* header {
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.logo {
    color: #222731;
    font-size: 26px;
    font-weight: 700;
}

.modeText {
    color: #4B6A9B;
    font-size: 13px;
    font-weight: 700;
    letter-spacing: 2.5px;
}

button {
    background-color: transparent;
    border: none;
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 10px;
    padding: 0;
}

.btn {
 width: 84px; 
    padding: 13px 16px;
    border-radius: 10px;
    background: #0079FF;
    border: none;
    color: #fff;
}

.iIcons i {
    position: absolute;
}

.iIcons {
    width: 100%;
    margin-bottom: 10px;
    border: 2px solid black;
    max-width: 700px;
    display: flex;
    padding: 5px 5px;
}

.icon {
    padding: 12px;
    color: #0079FF;
    min-width: 50px;
    height: 20px;
    text-align: center;
    margin-top: 11px;
} */

.inputArea {
    max-width: 700px ;
    width: 100%;
    margin-top: 10px;
    padding: 10px 5px 10px 40px;
    text-align: center;
    /* background-color: transparent; */
    border: none;
    color: #FFF;
    font-size: 13px;
    font-weight: 400;
    line-height: 25px;
    text-align: start;
}

.container {
    margin: 35px 0 14px 0;
    display: flex;
    flex-direction: column;
    gap: 20px;
    border-radius: 15px;
    border: 2px solid black;
    

}

.profile {
    display: grid !important;
    border-radius: 15px;
    /* background: #1E2A47; */
    gap: 20px 20px;
    padding: 7% 5%;
    background: #FEFEFE;
box-shadow: 0px 16px 30px -10px rgba(70, 96, 187, 0.20);
}

.image {
    grid-column: 1 / 2;
}

.profileImage {
    width: 70px;
    height: 70px;
}

.userDetails {
    grid-column: 2 / 12;
}

.userName {
    color: #FFF;
    font-size: 16px;
    font-weight: 700;
}

.page {
    color: #0079FF;
    font-size: 13px;
    font-weight: 400;
}

.dateJoined {
    color: #FFF;
    font-size: 13px;
    font-weight: 400;
}

.profileDetails {
    grid-column: 1 / 12;
    color: #FFF;
    font-size: 13px;
    font-weight: 400;
    line-height: 25px;
}


.dataList {
    grid-column-start:1;
    grid-column-end:12;
    padding: 15px  32px;
    display: flex;
    justify-content: space-between;
    border-radius: 10px;
    /* background: #141D2F; */
background: #F6F8FF;
}

.repos {
    display: flex;
    flex-direction: column;
    gap: 10px;
}

.repos.data {
    color: #FFF;
    text-align: center;
    font-size: 11px;
    font-weight: 400;
}

.repos.number {
    color: #FFF;
    font-size: 16px;
    font-weight: 700;
}

.footer {
    grid-column: 1 / 12;
    display: grid;
    grid-template-columns: 1fr;
    gap: 10px;
}

.footer p {
    color: #FFF;
    font-size: 13px;
    font-weight: 400;
    display: flex;
    align-items: center;
    gap: 15px;

}

@media (min-width: 490px) {
    .footer {
        grid-template-columns: repeat(2, 1fr);
    }

    .profileImage {
        width: 117px;
        height: 117px;
    }

    .userDetails {
        font-size: 26px;
    }

    .page {
        font-size: 16px;
    }

    .dateJoined {
        font-size: 15px;
    }

    .profileDetails {
        font-size: 15px;
    }

    .repos .data {
        font-size: 13px;
    }

    .repos .number {
        font-size: 22px;
    }
}

@media (min-width: 768px) {
    .footer {
        grid-template-columns: repeat(2, 1fr);
    }

    .profileImage {
        width: 117px;
        height: 117px;
    }

    .userDetails {
        font-size: 26px;
    }

    .page {
        font-size: 16px;
    }

    .dateJoined {
        font-size: 15px;
    }

    .profileDetails {
        grid-column: 2 / 12;
        font-size: 15px;
    }

    .dataList {
        grid-column: 2 / 12;
    }

    .userName {
        display: flex;
        justify-content: space-between;
    }

    .profileDetails {
        font-size: 15px;
    }

    .repos.data {
        font-size: 13px;
    }

    .repos.number {
        font-size: 22px;
    }

    .footer {
        grid-column: 2 / 12;
        grid-template-columns: repeat(2, 1fr);
    }
}
</style>







































