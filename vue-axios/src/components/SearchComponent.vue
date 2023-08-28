<script setup>


</script>

<template>
    
        <div class="searchbar">
            <form action="" class="search">
                <slot></slot>
            </form>
        </div>
        
</template>

<style scoped>
.content {
    margin: 35px 0 14px 0;
    display: flex;
    flex-direction: column;
    gap: 20px;
    border-radius: 15px;
}

.searchbar {
    border-radius: 15px;
    padding: 0 10px;
    background: #1E2A47;
}

.search {
    display: flex;
    align-items: center;
    justify-content: center;
}


</style>