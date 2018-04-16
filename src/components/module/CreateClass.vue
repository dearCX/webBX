<template>	
	<div class="right">
		<div class="classCont">
			<p>
				微课程是平台打造的特色课程，是基于一门学科/课程的某个重要的专题（或某个单元、主题等）而设计开发的一种微型化的在线视频网络课程。微课程是指由基于某个专题的系列化、连续性、层次化的微课构成。某个专题的微课程一般有5-10节微课组成（具体数量因学科、学习对象、专题内容等而定），这些微课可以向学生传授一个相对完整的知识专题或总结复习，非常适合学生的自主学习、意义建构及成绩提升。
			</p>
			<button class="create" @click="toCreateClass">创建微课程</button>				
			<ul class="classList" v-if="minClassList.length>0">
				<li v-for="item of minClassList">						
					<div class="classImg">						
						<div>
							{{item.name}}
						</div>
						<p>
							<a href="javascript:void(0);" class="select" @click="toViewClass(item.id)">查看</a>							
							<a href="javascript:void(0);" class="select" v-if="item.verifyStatus == 0 || item.verifyStatus == 3" @click="toEditClass(item)">编辑</a>
							<a href="javascript:void(0);" class="select-passing" v-if="item.verifyStatus == 1">审核中</a>
							<a href="javascript:void(0);" class="select-pass" v-if="item.verifyStatus == 2">审核通过</a>
							<a href="javascript:void(0);" class="select-nopass" v-if="item.verifyStatus == 3">审核未通过</a>
						</p>
					</div>
					<div class="classTitle">
						<p>{{item.name}}</p>
						<p>{{item.periodName}}&nbsp;&nbsp;{{item.videoNums}}节</p>
						<p>
							价格：￥
							<span v-if="item.money == 0">&nbsp;0.00</span>
							<span v-if="item.money > 0">&nbsp;{{item.money | moneyChange}}</span>
						</p>
					</div>
				</li>
			</ul>
		</div>	
		<Page :total="totalCount" show-elevator show-total v-if="minClassList.length>0" @on-change="changePage"></Page>		
	</div>	
</template>
<script>
import qs from "qs"
export default {
	name:'CreateClass',
	data(){
	  	return {
		  	minClassList:[
				// {title:'备战高考',info:'高三8节',price:'99.00'},
				// {title:'备战高考',info:'高三8节',price:'99.00'},
				// {title:'备战高考',info:'高三8节',price:'99.00'},
				// {title:'备战高考',info:'高三8节',price:'99.00'}
			],
			msg:{				
				reqError:'请求失败请重试',
				resError:'请求资源失败，请重试'
			},
			params:{				
				pageIndex:1,
				pageSize:10,
				token:"354374bbf8b6e0ef44b26e13eb1900cb674df11abdc98cf4f79a64a78952d3886943ba77c3f87fb94d45cf2aa30b11610662c6fa2a974a261019f03c72a9cb066fd16b92ae1c1cf28228c026138f73b739e5a7e794ac4b05ad52b7f62056135b1a127020233d4a4ec8c717953888324ad31911382e8f3060810ec7d6a50b775a0c499c805df9d0bb77651f5931a3a1433d6184f3555cc9d908bb4fb24aba4adc08311f5505777ccab3fbefbed52b46b4fa749c72b6f1cd2426bb759ed73b94f8d863cbf69239fa5864a65263c548507827629f1852ae0aea0b038f0691ff346098dd4d940ef1c265"
			},
			totalCount:'',
	  	}
	},
	filters: {
		moneyChange:function(value){
			if (!value){ return ''}
			return (value/100).toFixed(2);
		},
		fillType: function (value) {
			if (!value){ return ''}
			if(value == 'doc'|| value == 'docx'){
				value = './static/imgs/resource/fileDoc.png'
			}else if(value == 'ppt'|| value == 'pptx'){
				value = './static/imgs/resource/filePpt.png'
			}else if(value == 'xls' || value == 'xlsx'){
				value = './static/imgs/resource/fileXls.png'
			}else if(value == 'pdf'){
				value = './static/imgs/resource/filePdf.png'
			}else if(value == 'jpg'){
				value = './static/imgs/resource/fileJpg.png'
			}else if(value == 'png'){
				value = './static/imgs/resource/filePng.png'
			}else if(value == 'mp3'){
				value = './static/imgs/resource/fileMp3.png'
			}else if(value == 'avi'||value == 'rmvb'||value == 'mp4'){
				value = './static/imgs/resource/fileVideo.png'
			}else if(value == 'zip'){
				value = './static/imgs/resource/fileZip.png'
			}else if(value == 'rar'){
				value = './static/imgs/resource/fileRar.png'
			}else if(value == 'txt'){
				value = './static/imgs/resource/fileTxt.png'
			}else{
				value = './static/imgs/resource/fileunkonw.png'
			}
			return value;
		},
		formatTime:function (input) {
			var d = new Date(input);
			var year = d.getFullYear();
			var month = d.getMonth() + 1;
			var day = d.getDate();
			// var day = d.getDate() <10 ? '0' + d.getDate() : '' + d.getDate();
			// var hour = d.getHours();
			// var minutes = d.getMinutes();
			// var seconds = d.getSeconds();
			return  year+ '-' + month + '-' + day;
		}
	},
    methods:{
		toCreateClass(){
			this.$router.push('/MySpace/CreateClassOne');			
		},
		toEditClass(item){			
			this.$router.push({
				path:'/MySpace/CreateClassOne',
				query:{
					name:item.name,
					courseId:item.id,
					periodId:item.periodId,
					subjectId:item.subjectId,
					versionId:item.versionId,
					introduction:item.introduction,
					gradeIds:item.gradeIds.join(','),
					price:item.money
				}
			});		
		},
		toViewClass(id){
			this.$router.push('/ClassDatile?courseId='+id);
		},
		myClassList(){
			this.$http.post('/web/course/a/listMyCourse.do',qs.stringify({				
				pageIndex:this.params.pageIndex,
				pageSize:this.params.pageSize,
				token:this.params.token
			})).then(res => {	
				if(res.status != 200){
					this.$Message.error(this.msg.reqError);
				}else{
					let result = res.data;
					if(result.status != 0){
						this.$Message.error(this.msg.resError);
					}else{	
						if(result.data.list instanceof Array && result.data.list.length>0){
							this.minClassList = result.data.list;
							this.totalCount = result.data.totalCount;

						}else{
							this.minClassList = [];
						}						
					}
				}				
			}).catch(function (error) {
				alert(error);
			});
		},
		changePage(page){
			this.params.pageIndex = page;
			this.myClassList();
		},
	},
	created(){
		this.myClassList();
	} 
}
</script>
<style scoped>
    .right{
		float: left;
		width: 940px;
		min-height: 500px;
		border: 1px solid #e9e9e9;
		margin-left: 20px;
		padding: 50px;
		background: #FFFFFF;
	}
	.classCont>p{		
		font-size: 14px;
		line-height: 32px;
		color: #666666;
		text-indent:2rem;
	}
	.create{
		width: 140px;
		height: 40px;
		margin-top: 20px;
		background: #4fa5fd;
		color: #FFFFFF;
		line-height: 40px;
		border: none;
		border-radius: 5px;
		font-size: 16px;
		cursor: pointer;
	}
	.classList{
		margin-top: 40px;
		overflow: hidden;
	}
	.classList li{
		float: left;
		width: 50%;
		height: 200px;
	}
	.classImg{
		width: 160px;
		height: 120px;
		float: left;
	}
	.classImg>div{
		background: url('../../assets/imgs/resource/proclassdefault.png') no-repeat center center;
		width: 160px;
		text-align: center;
		height: 120px;
		line-height: 120px;
		font-weight: bold;
		margin-bottom: 8px;
		font-size: 16px;
		overflow: hidden;
		text-overflow:ellipsis;
		white-space: nowrap;
	}
	.classImg p{
		text-align: center;
	}
	.select{
		color: #666;		
		font-size: 14px;
	}
	.select{
		color: #4fa5fd;		
		font-size: 14px;
	}
	.select-passing{
		color: #ffbd5f;
		font-size: 14px;
	}
	.select-pass{
		color: #41b77e;	
		font-size: 14px;
	}
	.select-nopass{
		color: #ff9191;	
		font-size: 14px;
	}
	.classTitle{
		float: left;
		margin-left: 20px;
	}
	.classTitle p:first-child{
		font-size: 16px;
		margin-top: 10px;
		color: #333333;
	}
	.classTitle p:nth-child(2){
		font-size: 14px;
		color: #666;
	}
	.classTitle p:last-child{
		margin-top: 10px;
		font-size: 14px;
		color: #666;
	}
	.classTitle p:last-child span{
		color: #ff5a5a;
		font-size: 20px;
		
	}
	.ivu-page{
		text-align: center;
	}
</style>

