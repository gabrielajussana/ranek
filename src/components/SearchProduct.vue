<template>
<form @submit.prevent="searchProducts">
    <input name="search" id="search" type="text" v-model="search" placeholder="Buscar...">
    <input id="lupa" type="submit" value="Search" @click="searchProducts">
</form>
</template>
<script>
import { Component, Vue } from 'vue-property-decorator'
@Component
class SearchProduct extends Vue{
    search = ""

     searchProducts(){
        this.$router.push({ query: { q: this.search } });
    }

}
export default SearchProduct
</script>
<style scoped>
    form {
        max-width: 600px;
        margin: 30px auto 60px auto;
        position: relative;
    }

    #search{
        width: 100%;
        padding: 20px;
    }

    #search:focus,
    #search:hover{
        transform: scale(1.1);
    }

    #lupa{
        width: 62px;
        height: 62px;
        background: url('../assets/search.svg') no-repeat center center;
        text-indent: -150px;
        border: none;
        cursor: pointer;
        position: absolute;
        top: 0px;
        right: 0px;
        box-shadow: none;
    }
</style>