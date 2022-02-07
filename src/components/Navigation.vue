<template>
    <div class="nav_wrapper">
        <h1>Movies Catalog</h1>
        <input  type="text" 
                v-model="$parent.filterMovies"
                @change="$parent.$emit('find-movies')">
        <div class="user_info">
            <img src="../assets/account.png" alt="logo" class="user_logo">
            <span>Vadim Denisovski</span>
        </div>
    </div>
</template>


<style scoped>
    .nav_wrapper {
        display: flex;
        justify-content: space-around;
        align-items: center;
        font-size: 1rem;
        background-color: aqua;
        max-width: 100%;
        width: 100%;
    }
    input {
        max-width: 100%;
        width: 60%;
    }
    h1 {
        font-size: 2rem;
    }
    .user_info {
        width: 10%;
        display: flex;
        justify-content: space-between;
    }
    .user_logo {
        width: 12%;
    }
</style>