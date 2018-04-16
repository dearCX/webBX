<template>
		
	
	<div class="mainContainer">
		<div class="left">
			<p class="centerTitle">个人中心</p>
			<ul>
				<li><a href="#" class="active">个人中心</a> </li>
				<li><a href="#">个人中心</a> </li>
				<li><a href="#">个人中心</a> </li>
				<li><a href="#">个人中心</a> </li>
				<li><a href="#">个人中心</a> </li>
				<li><a href="#">个人中心</a> </li>
				<li><a href="#">个人中心</a> </li>
			</ul>
		</div>
		
		<div class="right">
			<p class="title">
				<a href="#">申请教师资格证</a> 
			</p>
			<p class="cont">
				教师资格证是教育行业从业教师的许可证。在我国，师范类大学毕业生须在学期期末考试中通过学校开设的教育学和教育心理学课程考试，并且要在全省统一组织的普通话考试中成绩达到二级乙等（中文专业为二级甲等）以上，方可在毕业时领取教师资格证。非师范类和其他社会人员需要在社会上参加认证考试等一系列测试后才能申请教师资格证。
			</p>
			<p class="cont">
				教师资格证是教育行业从业教师的许可证。在我国，师范类大学毕业生须在学期期末考试中通过学校开设的教育学和教育心理学课程考试，并且要在全省统一组织的普通话考试中成绩达到二级乙等（中文专业为二级甲等）以上，方可在毕业时领取教师资格证。非师范类和其他社会人员需要在社会上参加认证考试等一系列测试后才能申请教师资格证。
			</p>
			
			<form class="teacherInfo">
				<p>
					教师教龄：
					<input type="text" class="age"/>
				</p>
				<p>
					级别证书：
					<input type="text" class="age"/>
				</p>
				<p>
					<span class="number">0/100</span>
					<span class="teacherInfo">教师简介：</span>
					<div contenteditable="true" class="eitab"></div>
				</p>
				<div style="clear: both;"></div>
				
				<p>
					<input type="submit" value="申请成为教师" class="teacher" />
				</p>
				
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
	
	.left{
		width: 240px;
		border: 1px solid #e9e9e9; 
		color: #666666;
		float: left;
	}
	.centerTitle{
		font-size: 20px;
		padding: 41px 100px 20px 60px;
		border-bottom: 1px solid #e9e9e9; 
	}
	.left ul li a{
		color: #666666;
		text-decoration: none;
		display: inline-block;
		padding: 24px 112px 24px 59px;
		font-size: 16px;
		border-bottom: 1px solid #e9e9e9;
	}
	.left ul li a.active{
		color: #50a7ff;;
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
	.cont{
		text-indent: 2rem;
		font-size: 14px;
		color: #666666;
		margin-top: 20px;
	}
	.teacherInfo{
		font-size: 14px;
		color: #666666;
		margin-top: 40px;
	}
	.teacherInfo .age{
		width: 350px;
		height: 30px;
		border: 1px solid #e9e9e9;
		padding: 5px;
		outline: none;
	}
	.teacherInfo p{
		margin-top: 20px;
	}
	.eitab{
		width: 360px;
		height: 80px;
		border: 1px solid #e9e9e9;
		float: left;
		outline: none;
		margin-top: 20px;
	}
	.teacherInfo{
		float: left;
		position: relative;
	}
	.number{
		position: absolute;
		top: 225px;
		right: 10px;
		font-size: 12px;
		color: #999999;
	}
	.teacher{
		width: 160px;
		height: 40px;
		background: #50a7ff;
		color: #fff;
		border: none;
		outline: none;
		margin-left: 160px;
		border-radius: 5px;
	}
</style>
	
	
