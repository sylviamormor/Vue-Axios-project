<script setup>

</script>

<template>
    <header>
        <h2 class="logo">devfinder</h2>
        <button class="toggler">
           <span class="text">light </span><span>
           <img class="sun" src="../assets/sun.png" alt=""></span>
        </button>
    </header>
</template>

<style scoped>
header{
    display: flex;
    justify-content: space-between;
    align-items: center;
}
    .logo{
        color: #FFF;
        font-size: 26px;
        font-weight: 700;
    }
    .text{
        color: #FFF;
        font-size: 13px;
        font-weight: 700;
        letter-spacing: 2.5px;
    }
    button{
        background-color: transparent;
        border: none;
        display: flex;
        align-items: center;
        justify-content: space-between;
        gap: 10px;
        padding: 0;
    }

</style>





























<!-- <script setup>

</script>

<template>
    <header>
        <h2 class="logo">devfinder</h2>
        <button class="mode">
           <span class="modeText">DARK </span><span>
            <img class="moon" src="../assets/moon.png" alt=""></span>
        </button>
    </header>
</template>

<style scoped>
header{
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.logo{
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
  
</style> -->