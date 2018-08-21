<template>
	<div class="page-swipe">
		<mt-swipe :show-indicators="false" :auto='3000'>
			<mt-swipe-item>
				<router-link to="/chinaleague">
					<img :src="bannerPicArray[0].imageUrl" alt="" />
				</router-link>
				<div class="item-title">单身狗薯片</div>
			</mt-swipe-item>
			<mt-swipe-item>
				<router-link to="/match">
					<img :src="bannerPicArray[1].imageUrl" alt="" />
				</router-link>
				<div class="item-title">饮料：小茗同学(认真搞笑)</div>
			</mt-swipe-item>
			<mt-swipe-item>
				<router-link to="/hotnews">
					<img :src="bannerPicArray[2].imageUrl" alt="" />
				</router-link>
				<div class="item-title">沁橙亮洁 按压式牙膏</div>
			</mt-swipe-item>
		</mt-swipe>
	</div>
</template>

<script>
	import { Swipe, SwipeItem } from 'mint-ui'	
	import url from '@/urlRouter.js'
	import axios from 'axios'
	
	export default{
		name:'',
		data(){
			return {
				bannerPicArray:[]
			}
		},
		components:{
			Swipe,
			SwipeItem
		},
		created(){
			axios({
				method:'get',
				url:'http://127.0.0.1/allPHP/phpbases/g_banner.php',
				responseType:'json'
			}).then((response)=>{
				for(var i=0;i<response.data.length;i++){
					this.bannerPicArray.push(response.data[i])
				}
				console.log(this.bannerPicArray)
			})
		}
	}
</script>

<style>
	.mint-swipe{
		height: 140px;
	}
	.mint-swipe-item img{
		width: 100%;
		height: 100%;
	}
	.item-title{
		color:#fff;
        font-size:15px;
        text-indent:10px;
        text-align:center;
        position:absolute;
        width:100%;
        height:30px;
        top:110px;
        line-height:30px;
        left:0px;
        display:block;
        background-color:rgba(0,0,0,0.5);
	}
</style>