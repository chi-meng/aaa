<template>
     <div>
        <input type="text" v-model="b">
        <button @click="add">添加</button>
        <ul>
            <li v-for="(val,index) in guo">{{val}} <button @click="c(index)">删除</button></li>
        </ul>    
    </div>
</template>

<script>
export default {
    data(){
        return{
             guo:["香蕉","苹果","鸭梨"],
            b:""
        }
            // a:12
        },
        methods:{
            add:function(){
                if(this.b==""||this.b=="null"){
                    alert("内容不能空")
                }else{
                    this.guo.push(this.b);
                }
                this.fruit=""
            },
            c:function(index){
                this.guo.splice(index,1)
            }

        }
    }
</script>

<style>
    ul li{
        list-style: none;
    }
</style>


