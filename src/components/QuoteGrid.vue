<template>
    <div class="row">
        <app-quote v-for="(quote,i) in quotes" @click.native="deleteQuote(i)">{{quote}}</app-quote>
    </div>
</template>

<script>
   import Quote from './Quote.vue';

   export  default {
       props:['quotes'],
       components:{
           appQuote:Quote
       },
       methods: {
           deleteQuote(index){
                this.$emit('quoteDeleted',index);
           }
       }
   }
</script>

<style scoped>

</style>