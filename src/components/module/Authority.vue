<template>
	<div class="mainContainer">
		<div class="right">
			<p class="title">
				<a href="#">访问权限</a> 
			</p>
			<div class="boderImg">
				<img src="img/headImg.png" width="350px" height="230px"/>
			</div>
			<p class="authority">设置谁可以访问我的空间</p>
			
			<p class="authorityInput">
				<input type="radio" name="authority" value="0" checked="checked"/><label>所有人可见</label>
				<input type="radio" name="authority" value="1" /><label>通讯录可见</label>
				<input type="radio" name="authority" value="2" /><label>仅自己可见</label>
			</p>
		</div>
		
	</div>
</template>
<style scoped>
	.mainContainer{
		width: 1200px;
		margin: auto;
		margin-top: 40px;
	}
	.right{
		width: 815px;
		padding: 40px 60px 40px 60px;
		height: 559px;
		border: 1px solid #e9e9e9;
		margin-left: 21px;
		float: left;
	}
	.right .title{
		font-size: 20px;
		color: #666666;
		border-bottom: 1px solid #e9e9e9; 
	}
	.right .title a{
		display: inline-block;
		text-decoration: none;
		font-size: 20px;
		color: #666666;
		padding-bottom: 20px;
		border-bottom: 1px solid #000; 
	}
	.boderImg{
		width: 350px;
		height: 230px;
		border: 1px solid #e9e9e9;
		margin-top: 40px;
		padding: 1px;
	}
	.authority{
		font-size: 14px;
		color: #999999;
		margin-top: 14px;
	}
	.authorityInput{
		font-size: 14px;
		color: #333333;
	}
	.authorityInput label{
		margin-left: 20px;
	}
	.authorityInput input:first-child{
		margin-left: 0px;
	}
	.authorityInput input{
		margin-top: 50px;
		margin-left: 120px;
	}
</style>
