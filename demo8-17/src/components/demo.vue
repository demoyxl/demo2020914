<template>
	<div class='box'>
			<div class="a">
				<div class="b" ref="demo1">1</div>
				<div class="b" ref="demo2">2</div>
				<div class="b" ref="demo3">3</div>
				<div class="b" ref="demo4">4</div>
				<div class="b" ref="demo5">5</div>
				<div class="b" ref="demo6">6</div>
				<div class="b" ref="demo7">7</div>
				<div class="b" ref="demo8">8</div>
				<div class="b" ref="demo9">9</div>
			</div>
			<el-button type="primary" @click="func()">开始</el-button>
			<el-button type="primary" @click="func1()">结束</el-button>
	</div>
</template>

<script>
	export default{
		data() {
			return{
				timer:null,
				r:'',
				arr:[],
				move:0
			}
		},
		methods:{
			func(){
				if(this.timer !== null){return;}
				this.timer=setInterval(()=>{
						//初始化九宫格
						this.func3();
						//随机9个数字，对应3组颜色
						this.func5();
						//产生三个随机数，并渲染宫格
						this.func4();
						//移除数组中的颜色值
						this.func6();
				},1000);
			},
			func6(){
				this.arr= []
			},
			func4(){
				var x=parseInt((Math.random()*8+1).toFixed(0));
				var y=parseInt((Math.random()*8+1).toFixed(0));
				var z=parseInt((Math.random()*8+1).toFixed(0));
				if( x!=y && y!=z && x!=z){
					this.func2(x,y,z);
				}else{
					this.func4();
				}
			},
			func3(){
				for(var i=1;i<=9;i++){
					var ss="demo"+i;
					this.$refs[ss].style.backgroundColor="#ddd";
				}
			},
			func5(){
				for(var i=0;i<9;i++){
					this.r=parseInt(Math.random()*256),
					this.arr.push(this.r)
				}
			},
			func2(x,y,z){
				var yu="demo"+x;
				var yy="demo"+y;
				var zz="demo"+z;
				this.$refs[yu].style.backgroundColor='rgb('+this.arr[0]+','+this.arr[1]+','+this.arr[2]+')';
				this.$refs[yy].style.backgroundColor='rgb('+this.arr[3]+','+this.arr[4]+','+this.arr[5]+')';
				this.$refs[zz].style.backgroundColor='rgb('+this.arr[6]+','+this.arr[7]+','+this.arr[8]+')';	
			},
			func1(){
				clearInterval(this.timer);
				this.timer = null
				this.func3();
			}
		}
	}
</script>

<style>
	.a{
		display: flex;
		flex-direction: row;
		flex-wrap: wrap;
		margin: 0 auto;
		justify-content: center;
		align-items: center;
		width: 50%;
	}
	.b{
		width: 30%;
		background-color:#ddd;
		margin: 5px;
		height: 0;
		padding-top:15%;
		padding-bottom: 15%;
	}
</style>
