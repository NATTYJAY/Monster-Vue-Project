<template>
    <div class="row alert alert-danger" v-if="show">
        <div class="row  red lighten-2 alert">
            <div class="col s11">
                <p>{{ messages }}</p>
            </div>
            <!--<div class="col s1">-->
                <!--<button type="button"><span class="fa fa-close" @click="show=false"></span></button>-->
            <!--</div>-->
        </div>
    </div>
</template>

<script>
    export default {
        name: "ErorrAlert",
        data:function () {
            return{
                show:false
            }
        },
        props:['messages'],
        methods:{
            showAlert:function () {
                this.show  = true;
                window.setTimeout(()=>{this.show =false },5000)
            }
        },
    }
</script>

<style scoped>

</style>