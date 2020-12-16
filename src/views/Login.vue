<template>
    <div class="container">
        <the-login/>
    </div>
    
</template>

<script>

import TheLogin from '../components/auth/TheLogin.vue';
export default {
    components:{
        TheLogin
    }
}
</script>

<style scoped>
    .container{
        display:flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
    }
</style>