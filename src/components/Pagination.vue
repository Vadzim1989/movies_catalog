<template>
    <ul class="pagin">
        <li><button @click="$parent.$emit('page-down')">Previous</button></li>
        <li><button @click="$parent.$emit('page-up')">Next</button></li>
    </ul>
</template>


<style scoped>
    .pagin > * {
        display: inline-block;
        text-decoration: none;
    }
    .pagin {
        margin-left: 45%;
    }
</style>