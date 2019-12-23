<template>
  <div class="container">
    <app-alert :messages="errorMessage" ref="errorAlert"></app-alert>
    <app-header :quoteCount="quotes.length" :maxQuote="maxQuotes"></app-header>
    <app-new-quote @quoteAdded="newQuote"></app-new-quote>
    <app-quote-grid :quotes="quotes" @quoteDeleted="deletedQuotes"></app-quote-grid>
    <div class="row">
      <div class="col-sm-12 text-center">
        <div class="alert alert-info">
          Info: Click on a Quote to delete it!
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import  QuoteGrid from './components/QuoteGrid.vue';
  import  NewQuote from './components/NewQuote.vue';
  import  Header from './components/Header.vue';
  import  Alert from './components/Alert.vue';


export default {
  data: function(){
      return {
          quotes:[
              'Just a quote to see something'
          ],
          maxQuotes:10,
          errorMessage: ''
      }
  },
    methods:{
        newQuote(quote){
            if(this.quotes.length >=this.maxQuotes){
                this.errorMessage = 'Please delete Quote first to continue adding';
                this.$refs.errorAlert.showAlert();
            }else{
                this.quotes.push(quote);
            }
        },
        deletedQuotes(index){
            this.quotes.splice(index,1);
        }
    },
    components:{
        appQuoteGrid: QuoteGrid,
        appNewQuote:NewQuote,
        appHeader:Header,
        appAlert:Alert
    }
}
</script>

<style>

</style>
