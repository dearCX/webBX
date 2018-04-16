<template>
	<div class="mainContainer">
		<div class="right">
			<p class="title">
				<a href="#">个人资料</a> 
			</p>
			<form>
				<div class="personCont">
					<img src="img/headImg.png" width="150px;" height="150px;" align="absbottom"/>
					<input type="button" class="up" value="上传头像"/>
					<span class="intro">"图像格式：jpg    png  gif    格式"</span>
				</div>
				<div class="personInfo">
					<p>账号：admin</p>
					<p>账号：admin</p>
					
					个性签名：
					<div contenteditable="true" id="infoDivs">
						无
					</div>
					<div style="clear: both;"></div>
					<input type="submit" value="编辑" id="update" />
				</div>
				
				
			</form>
			
			
			
			
			
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
	.personCont{
		width: 826px;
		padding-top: 30px;
		margin: auto;
	}
	.up{
		width: 160px;
		height: 40px;
		background: #50a7ff;
		color: #fff;
		border: none;
		outline: none;
		margin-left: 30px;
		margin-right: 30px;
		border-radius: 5px;
	}
	.intro{
		font-size: 14px;
		color: #999999;
	}
	.personInfo{
		width: 385px;
		height: 360px;
		margin-left: 188px;
		color: #666666;
	}
	.personInfo p{
		height: 70px;
		line-height: 70px;
		font-size: 14px;
		
	}
	#infoDivs{
		width: 350px;
		height: 98px;
		border: 1px solid #e9e9e9; 
		margin-top: 10px;
		color: #999999;
		outline: none;
		padding: 5px;
	}
	#update{
		width: 86px;
		height: 32px;
		background: #47a2ff;
		color: #FFFFFF;
		border: none;
		margin-top: 20px;
		margin-left: 274px;
	}
</style>

