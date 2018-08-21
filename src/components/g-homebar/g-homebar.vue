<template>
	<div class="type-bar">
		<div v-for="(cate,index) in category">
			<img v-lazy="cate.image" width="90%" />
			<span>{{cate.mallCategoryName}}</span>
		</div>
	</div>
</template>

<script>
	export default{
		props:['homebarData'],
		name:'g-homebar',
		data(){
			return {
				category:null
			}
		},
		components:{
			
		},
		created(){
			this.category=this.homebarData
			//console.log(this.category)
		},
		watch:{
            homebarData:function(val){
                this.category=this.homebarData
				//console.log(this.category) 
            }
        }
	}
	
</script>

<style>
	.type-bar{
		margin-top: -5px;
		width: 100%;
		/*background: linear-gradient(left,#f125A8,#F542D6);*/
      	border-radius: 0  0 .5rem .5rem;
      	font-size:14px;
      	display: flex;
     	flex-direction:row;
      	flex-wrap:nowrap;
	}
	.type-bar div{
		padding: .3rem;
      	font-size: 12px;
      	text-align: center;
      	color: #010;
      	font-weight: 400;
	}
	.type-bar div:first-child img{
		width: 57.5px;
	}
</style>