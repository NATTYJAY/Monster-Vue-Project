<template>
    <div class="row">
        <form>
            <app-alert :messages="errorMessage" ref="errorAlert"></app-alert>
            <div class="col-sm-8 col-sm-offset-2 col-xs-12 col-md-6 col-md-offset-3 form-group">
                <label>Quote</label>
                <textarea class="form-control" rows="3" v-model="quote"></textarea>
            </div>
            <div class="col-sm-8 col-sm-offset-2 col-xs-12 col-md-6 col-md-offset-3 form-group">
                <button class="btn btn-primary" @click.prevent="createNew">Add quote</button>
            </div>
        </form>
    </div>
</template>

<script>
    import  Alert from './../components/Alert.vue';
    export  default {
    data:function(){
        return{
            quote:'',
            errorMessage: ''
        };
    },
        methods:{
        createNew(){
            if(this.quote === ''){
                this.errorMessage = 'Quote cannot be empty';
                this.$refs.errorAlert.showAlert();
            }else{
                this.$emit('quoteAdded', this.quote); // Send new quote to the parent component.
                this.quote = '';
            }

        }
        },
        components:{
            appAlert:Alert
        }
    }
</script>

<style scoped>

</style>