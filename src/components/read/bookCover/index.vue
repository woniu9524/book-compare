<template>
    <el-card :body-style="{ padding: '0px' }" class="card-style" @click="goBook">
        <el-image
                style="width: 100%; height: 220px"
                :src="'http://localhost:4000/bookCovers/'+url"
                fit="fill"
                class="image"
        ></el-image>
        <div style="text-align: center">
            <el-button type="text" @click="goBook">{{bookName}}</el-button>
        </div>
    </el-card>
</template>

<script>
    import {defineComponent} from "@vue/runtime-core";

    export default defineComponent( {
        name: "index",
        props:{
            url:{
                type:String,
                default:'http://localhost:4000/bookCovers/default.png'
            },
            bookName:{
                type:String,
                default: '无'
            },
            bookId:{
                type:String,
                default:-1,
            },
        },
        methods:{
            goBook(){
                this.$router.push({path:'/book/read',query:{'bookId':this.bookId}})
            }
        }
    })
</script>

<style scoped>
    .card-style{
        width: 200px;
        height: 250px;
        margin: 20px 20px 20px 20px;
        display: inline-block;
    }
    .image {
        display: block;
    }
</style>
