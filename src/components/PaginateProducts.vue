<template>
    <ul v-if="pagesTotal > 1">
        <li v-for="page in pagesTotal" :key="page">
            <router-link :to="{query: query(page)}">{{page}}</router-link>
        </li>
    </ul>
</template>
<script>
import { Vue, Prop, Component } from 'vue-property-decorator'
@Component
class PaginateProducts extends Vue {
    @Prop({ type: Number, default: 1 }) productsPerPage
    @Prop({ type: Number, default: 1 }) productsTotal 

     query(page){
        return {
            ...this.$route.query,
            _page: page
        };
     }

    get pages(){
        const current = Number(this.$route.query._page);
        const range = 9;
        const offset = Math.ceil(range / 2);
        const total = this.pagesTotal;
        const pagesArray = [];

        for(let i = 1; i <= total; i++){
            pagesArray.push(i)
        }

        pagesArray.splice(0 , current - offset);
        pagesArray.splice(range, total);

        return pagesArray;
    }


    get pagesTotal(){
        const total = this.productsTotal / this.productsPerPage;
        return (total !== Infinity)? Math.ceil(total): 0;
    }
}
export default PaginateProducts
</script>
<style scoped>
    ul {
        grid-column: 1/-1;
    }
    li{
        display: inline-block;
    }

    li a {
        padding: 2px 8px;
        border-radius: 2px;
        margin: 4px;
    }

    li a.router-link-exact-active,
    li a:hover{
        background: #87F;
        color: #FFF;
    }
</style>