<template>
    <header>
        <nav>
            <router-link to="/" class="logo">
                <img src="@/assets/ranek.svg" alt="Ranek">
            </router-link>
            <router-link to="/login" class="btn"> Vender / Login</router-link>
        </nav>
    </header>
</template>
<script>
import { Component, Vue } from 'vue-property-decorator'
@Component
class TheHeader extends Vue{
    
}
export default TheHeader
</script>
<style scoped>
    nav {
        display: flex;
        align-items: center;
        justify-content: space-between;
        padding: 15px 20px;
        box-shadow: 0 2px 4px rgba(30, 60, 90, .2);
    }

    .logo {
        padding: 10px 0px;
    }

    .logo img {
            width: 90px;
        }
</style>