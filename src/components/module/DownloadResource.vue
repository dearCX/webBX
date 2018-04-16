<template>	
	<div id="right-resource">
		<div class="right-title">
			<p>
				<a href="#" class="active">同步资源</a>
				<a href="#">知识点</a>
				<a href="#">特色微课</a>
			</p>
			<div>
				<select class="select">
					<option>全部学科</option>
				</select>
				<input placeholder="请输入资源名称" class="txt"/>
				<button>搜索</button>
			</div>
		</div>
		<div class="operator">	
			<button @click="showBatch" :class="{active:ifBatch==true}">批量设置</button>
		</div>		
		<div class="batch-modify" v-if="ifBatch">
			<Checkbox v-model="single">全选</Checkbox>			
			<span>推送</span>			
			<span>删除</span>
		</div>
		<ul class="resourceCont">
			<li v-for="item of resourceList">
				<div>
					<img src="../../assets/imgs/space/headImg.png"/>				
					<div class="doc-content">
						<p class="doc-title">
							<span>{{item.title}}</span> 
							<button>课件</button>
						</p>
						<div class="sub-title">
							<span>{{item.class}}</span>
							<span>{{item.title}}</span>
							<span>{{item.subject}}</span>
							<span>{{item.version}}</span>
							<span>{{item.book}}</span>
							<span>{{item.section}}</span>
							<span>{{item.content}}</span>
							<span class="upTime">收藏时间：{{item.date}}</span>
						</div>
						<div class="edit">
							<p class="edit-title">
								<span>编辑</span> 
								<Icon type="arrow-down-b" color="#1caaf1"></Icon>
							</p>
							<div class="edit-content">
								<span>推送</span>
								<span>删除</span>
							</div>			
						</div>								
					</div>	
				</div>									
			</li>
		</ul>
		<Page :total="100" show-elevator show-total></Page>	
	</div>
	
</template>
<script>
export default {
  	name:'DownloadResource',
  	data(){
	  	return {
		  	resourceList:[
			  	{title:'前端从入门到放弃.doc',class:'初中',subject:'数学',version:'人教版',book:'七年级上册',section:'第一章',subTitle:'方程式',content:'一元一次方程',date:'2019-01-01'},
			  	{title:'前端从入门到放弃.doc',class:'初中',subject:'数学',version:'人教版',book:'七年级上册',section:'第一章',subTitle:'方程式',content:'一元一次方程',date:'2019-01-01'},
			  	{title:'前端从入门到放弃.doc',class:'初中',subject:'数学',version:'人教版',book:'七年级上册',section:'第一章',subTitle:'方程式',content:'一元一次方程',date:'2019-01-01'},
			    {title:'前端从入门到放弃.doc',class:'初中',subject:'数学',version:'人教版',book:'七年级上册',section:'第一章',subTitle:'方程式',content:'一元一次方程',date:'2019-01-01'},
				{title:'前端从入门到放弃.doc',class:'初中',subject:'数学',version:'人教版',book:'七年级上册',section:'第一章',subTitle:'方程式',content:'一元一次方程',date:'2019-01-01'},
				{title:'前端从入门到放弃.doc',class:'初中',subject:'数学',version:'人教版',book:'七年级上册',section:'第一章',subTitle:'方程式',content:'一元一次方程',date:'2019-01-01'}
		  	],
			ifBatch:false,  
			single:false, 
	  	}
  	},
	methods:{
		showBatch(){
			if(!this.ifBatch){
				this.ifBatch = true;
				this.single = false;				
			}else{
				this.ifBatch = false;
				
			}
		}
	}   
}
</script>
