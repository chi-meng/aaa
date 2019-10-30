<template>
    <div>
    <button @click="sub">-</button>
    <span>{{num}}</span>
    <button @click="add">+</button>
    </div>
</template>
<script>
export default {
    name:"chen",
    data(){
        return{
            num:0
        };
    },
     methods:{
            add(){
                this.num++
            },
            sub(){
                if(this.num>0){
                    this.num--
                }
            }
        }
}
</script>
<style>

</style>


