<template>
   <div class="col-md-6">
            <h1>商品列表</h1>
            <table class="table table-bordered">
                <tr>
                    <th style="text-align: center">商品名称</th>
                    <th style="text-align: center">商品单价</th>
                    <th style="text-align: center">商品数量</th>
                    <th style="text-align: center">添加至购物车</th>
                </tr>
                <tr v-for='val,ind in fruitlist'>
                    <td>{{val.name}}</td>
                    <td>{{val.price}}</td>
                    <td>
                        <btn v-bind:count="val.count" v-bind:ind="ind" @add-count='add' @sub-count='sub'></btn>
                    </td>
                    <td><button @click="addcart(ind)" class="btn btn-primary btn-sm">添加至购物车</button></td>
                </tr>
            </table>
        </div>
</template>

<script>
import btn from "./btn.vue"
import bus from "../bus.js"
export default {
    components:{
        btn
    },
    data() {
        return {
            fruitlist: [
                { name: "香蕉", price: "2.3", count: 0 },
                { name: "苹果", price: "2.0", count: 0 },
                { name: "鸭梨", price: "2.5", count: 0 },
                ]
            }
        },
        methods:{
            add(i) {
                this.fruitlist[i].count++

            },
            sub(i) {
                
                if(this.fruitlist[i].count > 0){ 
                    this.fruitlist[i].count--
                }
            },
            clone(obj) {
                var newobj = {};
                for (var i in obj) {
                    newobj[i] = obj[i]
                }
                return newobj;
            },
            addcart(i) {
                var fruit = this.clone(this.fruitlist[i])
                bus.$emit("cartevent", fruit)
            }
        }
}
</script>

<style>
    th{
        text-align: none;
    }
</style>