<template>
   <div class="col-md-6">
            <h1>购物车列表</h1>
            <table class="table table-bordered">
                <tr>
                    <th style="text-align: center">商品名称</th>
                    <th style="text-align: center">商品单价</th>
                    <th style="text-align: center">商品数量</th>
                    <th style="text-align: center">删除</th>
                </tr>
                <tr v-for='val,ind in cartlist'>
                    <td>{{val.name}}</td>
                    <td>{{val.price}}</td>
                    <td>
                        <btn v-bind:count="val.count" v-bind:ind="ind" @add-count='add' @sub-count='sub'></btn>
                    </td>
                    <td><button @click='del(ind)' class="btn btn-danger btn-sm">删除</button></td>
                </tr>
            </table>
            <button class="btn btn-success" @click="total">结算</button>
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
                cartlist: [],
            }
        },
        mounted() {
            var self = this;
            bus.$on("cartevent", (data) => {
                for (var i = 0; i < self.cartlist.length; i++) {
                    if (self.cartlist[i].name == data.name) {
                        self.cartlist[i].count += data.count;
                        return;
                    }
                }

                self.cartlist.push(data)
            })
        },
        methods: {
            add(i) {
                this.cartlist[i].count++

            },
            sub(i) {
                if (this.cartlist[i].count > 0) {
                    this.cartlist[i].count--
                }

            },
            del(i) {
                this.cartlist.splice(i, 1)
            },
            total() {
                var result = 0;
                for (var i = 0; i < this.cartlist.length; i++) {
                    result += this.cartlist[i].count * this.cartlist[i].price;
                }
                result = result.toFixed(2);
                alert("您一共消费了" + result)
            }
        }
}
</script>

<style>

</style>