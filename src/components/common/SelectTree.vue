<template>
    <div>
        <div id="load-resource">
            <div class="left">
                <div>                  
                </div> 
                <ul class="section" v-if="nodeTree.length<1"> 
					<li>暂无任何资源数据</li>  
				</ul>                
				<ul class="section" v-if="nodeTree.length>0">
					<li v-for="item of nodeTree">
						<div>
							<b @click="unfold1(item)" class="fold">
								<Icon type="ios-plus-outline" size=20 v-if="item.children.length>0"></Icon>
							</b>                            
							<span @click="tabLoad1(item)" :class="{active:item.id==loadId1}">{{item.name}}</span>								
						</div>
						<ul class="joint" v-if="item.children.length>0" :class="{active:item.id == foldId1}">
							<li v-for="item of item.children">
								<div>
									<b @click="unfold2(item)" class="fold">
										<Icon type="ios-plus-outline" size=20 v-if="item.children.length>0"></Icon>
									</b>  
									<span @click="tabLoad2(item)" :class="{active:item.id==loadId2}">{{item.name}}</span>										                                  
								</div>
								<ul class="bar-line" v-if="item.children.length>0" :class="{active:item.id == foldId2}">
									<li v-for="item of item.children">                                        
										<span @click="tabLoad3(item)" :class="{active:item.id==loadId3}">{{item.name}}</span>											 
									</li>
								</ul>                               
							</li>
						</ul>
					</li>
				</ul>
            </div>
        </div>
    </div>
</template>
<script>
import qs from "qs"
export default {
  name:'SelectTree',
    data(){
         return {
            params:{	
				token:this.$storage.getStorage("token")
			},
            subjectList:[],
			bookList:[],
			textBookList:[],
			periodId:2,
			subjectId:2,
			bookId:'',
			textBookId:'',
			period:'',
			subject:'',
			book:'',
			texBook:'',
			classList:[
				{id:1,name:'高中'},
				{id:2,name:'初中'},
				{id:3,name:'小学'},
			],			
			selData:'',           
            nodeTree:[],
            loadId1:'',
			loadId2:'',
			loadId3:'',
            foldId1:'',
            foldId2:''
        }
    },
    methods:{
        tabLoad1(item){
            this.loadId1 = item.id;  
			this.loadId2 = '';
			this.loadId3 = '';
			if(this.resourceKindId == 1){
                this.bid1 = item.id; 
                this.bname1 = item.name;           
			}else if(this.resourceKindId == 2){
                this.kid1 = item.id;
                this.kname1 = item.name; 
            }
            this.fileName = item.name;
            this.getUniCode();
        },
		tabLoad2(item){
            this.loadId2 = item.id; 
			this.loadId1 = '';
			this.loadId3 = ''; 
			if(this.resourceKindId == 1){
                this.bid2 = item.id; 
                this.bname2 = item.name;              
			}else if(this.resourceKindId == 2){
                this.kid2 = item.id;
                this.kname2 = item.name; 
            }
            this.fileName = item.name;
            this.getUniCode();
        },
		tabLoad3(item){
            this.loadId3 = item.id; 
			this.loadId1 = '';
			this.loadId2 = ''; 
			if(this.resourceKindId == 1){
                this.bid3 = item.id;
                this.bname3 = item.name;              
			}else if(this.resourceKindId == 2){
                this.kid3 = item.id;
                this.kname3 = item.name; 
            }
            this.fileName = item.name;
            this.getUniCode();
        },
		unfold1(item){              
            this.foldId1 = item.id;
        },
        unfold2(item){              
            this.foldId2 = item.id;
        },            
        getResourceList(){
            this.$http.post('/web/coursebook/listResourceLocal.do',qs.stringify({				
				periodId:this.periodId,
				subjectId:this.subjectId,				
				withDisabledNode:1
			})).then(res => {	
				if(res.status != 200){
					this.$Message.error('请求失败请重试');
				}else{
					let result = res.data;
					if(result.status != 0){
						this.$Message.error('请求资源失败，请重试');
					}else{	
						if(result.data.children instanceof Array && result.data.children.length>0){
                            this.nodeTree = result.data.children;
						}else{
							this.nodeTree = [];
						}						
					}
				}			
				
			}).catch(function (error) {
				alert(error);
			});
        },            
        getKnowTree(){
            this.$http.post('/web/coursebook/getKnowledgePointTree.do',qs.stringify({				
				periodId:this.periodId,
				subjectId:this.subjectId,				
				withDisabledNode:1
			})).then(res => {	
				if(res.status != 200){
					this.$Message.error('请求失败请重试');
				}else{
					let result = res.data;
					if(result.status != 0){
						this.$Message.error('请求资源失败，请重试');
					}else{	
						if(result.data.children instanceof Array && result.data.children.length>0){
                            this.nodeTree = result.data.children;
						}else{
							this.nodeTree = [];
						}						
					}
				}			
				
			}).catch(function (error) {
				alert(error);
			});
        },
        getNodeTree(){
            this.$http.post('/web/coursebook/getBookNodeTree.do',qs.stringify({				
				periodId:this.periodId,
				subjectId:this.subjectId,
				versionId:this.bookId,
				textbookId:this.textBookId,
				withDisabledNode:1
			})).then(res => {	
				if(res.status != 200){
					this.$Message.error('请求失败请重试');
				}else{
					let result = res.data;
					if(result.status != 0){
						this.$Message.error('请求资源失败，请重试');
					}else{	
						if(result.data.children instanceof Array && result.data.children.length>0){
                            this.nodeTree = result.data.children;
						}else{
							this.nodeTree = [];
						}						
					}
				}			
				
			}).catch(function (error) {
				alert(error);
			});
        },
        getSubjectList(periodId){
			this.$http.post('/web/coursebook/listPeriod2Subject.do',qs.stringify({				
				periodId:periodId,
				name:'',
				status:1,
				pageIndex:1,
				pageSize:100
			})).then(res => {	
				if(res.status != 200){
					this.$Message.error('请求失败请重试');
				}else{
					let result = res.data;
					if(result.status != 0){
						this.$Message.error('请求资源失败，请重试');
					}else{	
						if(result.data.list instanceof Array && result.data.list.length>0){
							this.subjectList = result.data.list;
							if(result.data.list.length == 1){
								this.open=false;
							}
						}else{
                            this.subjectList = [];
                            this.nodeTree = []
                            this.open=false;
						}						
					}
				}			
				
			}).catch(function (error) {
				alert(error);
			});
		},	
		getBookList(subjectId){
			this.$http.post('/web/coursebook/listBookVersion.do',qs.stringify({				
				periodId:this.periodId,
				subjectId:subjectId,
				name:'',
				status:1,
				pageIndex:1,
				pageSize:100
			})).then(res => {	
				if(res.status != 200){
					this.$Message.error('请求失败请重试');
				}else{
					let result = res.data;
					if(result.status != 0){
						this.$Message.error('请求资源失败，请重试');
					}else{	
						if(result.data.list instanceof Array && result.data.list.length>0){
							this.bookList = result.data.list;							
						}else{
                            this.bookList = [];
                            this.nodeTree = []
                            this.open=false;
						}
						
					}
				}			
				
			}).catch(function (error) {
				alert(error);
			});
		},
		getTextBookList(versionId){
			this.$http.post('/web/coursebook/listTextbook.do',qs.stringify({				
				periodId:this.periodId,
				subjectId:this.subjectId,
				versionId:versionId,
				name:'',
				status:1,
				pageIndex:1,
				pageSize:100
			})).then(res => {	
				if(res.status != 200){
					this.$Message.error('请求失败请重试');
				}else{
					let result = res.data;
					if(result.status != 0){
						this.$Message.error('请求资源失败，请重试');
					}else{							
						if(result.data.list instanceof Array && result.data.list.length>0){
							this.textBookList = result.data.list;							
						}else{
                            this.textBookList = [];
                            this.nodeTree = []
                            this.open=false;
						}
					}
				}			
				
			}).catch(function (error) {
				alert(error);
			});
        },
        getsubject(id,name){      
			this.bookList = [];
			this.textBookList = [];
			this.subjectId = '';
			this.period = name;
			this.periodId = id;
            this.getSubjectList(id);
		},
		getbook(id,name){
			this.textBookList = [];
			this.bookId = '';
			this.subject = name;
            this.subjectId = id;
            if(this.resourceKindId == 1){
                this.getBookList(id);
            }else if(this.resourceKindId == 2){
                this.selData = this.period+'/'+this.subject;
                this.open = false;
                this.getKnowTree();   
            }
		},
		gettexBook(id,name){
			this.book = name;
			this.bookId = id;
			this.getTextBookList(id);
		},
		seltexBook(id,name){
			this.textBookId = id;
			this.texBook = name;
			this.selData = this.period+'/'+this.subject+'/'+this.book+'/'+this.texBook;
            this.open = false;
            this.getNodeTree();
		}
    },
    created(){
    	this.getKnowTree()
    }
}
</script>
<style scoped>
#load-resource{
    min-height: 900px;
    overflow-y:auto;
}
.section{
    width: 100%;
    height: 550px;    
    overflow-y:auto;
}
.section li{
    margin: 10px;  
}
.joint>li{
    margin-right: 0;  
}
.bar-line>li{
    margin-right: 0;  
}
.section li .ivu-icon-ios-plus-outline{
   cursor: pointer;
}
.section li p{
    float: right;
    cursor: pointer;
    display: none;
    margin-top: 3px;
}
.section li p.active{
    display: block;
}
.section li span{
    cursor: pointer;
}
.section li span.active{
    color: #47a2ff;
}
.section li .ivu-icon-ios-cloud-upload-outline{
    color: #47a2ff;    
}
.fold{
    display: inline-block;
    width: 18px;
    height: 20px;
}
.joint,.bar-line{
    display: none;
}
.joint.active,.bar-line.active{
    display: block;
}
.uploader-example .uploader-btn{
    margin: 10px 0;
    display: none;
}
.uploader-example .uploader-btn.active{
    display: block;
    color: #fff;    
    background-color: #f90;
    border-color: #f90;
}
.uploader-example .uploader-btn.active:hover{
    background-color: #ffad33;
    border-color: #ffad33;
}
.uploader-example .uploader-list {
    max-height: 440px;
    overflow: auto;
    overflow-x: hidden;
    overflow-y: auto;
}
</style>


