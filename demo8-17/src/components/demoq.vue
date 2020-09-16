<template>
	<div>
		<br>
		<br>
		<div class="yu">{{message}}</div>
		<button @click="qq">点击监听</button>
	</div>
</template>

<script>
	export default{
		data() {
			return {
				message:'你好'
			}
		},
		methods:{
			qq(){
				this.message="nihao8yue18";
				var obj = {
						
						}
						//为_age设置一个代理age，改变_age提供age即可
						Object.defineProperty(obj,"age",{
							configurable:true,//属性可配置
							set:function(v){
								console.log("age发生了改变")
								this._age=v;
							},
							get:function(){
								return this._age;
							}
						})
						obj.age = 13;
			}
		}
	}
</script>

<style>
</style>
