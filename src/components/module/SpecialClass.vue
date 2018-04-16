<template>
    <div>
        <div id="filter-list" class="w-1200">
            <div>
                <p>
                    <Icon type="ios-list-outline"></Icon>
                    <span>类型</span>
                </p>
                <ul>
                    <li v-for="item of allType" @click="changeType(item)" :class="{active:item.id==selType}">{{item.name}}</li>
                </ul>
            </div>
            <div v-if="selType ==1">
                <p>
                   <Icon type="ios-list-outline"></Icon>
                    <span>学段</span>
                </p>
                <ul>
                    <li v-for="item of periodList" @click="changePeriod(item)" :class="{active:item.id==selPeriod}">{{item.name}}</li>
                </ul>
            </div>
            <div v-if="selType ==1">
                <p>
                    <Icon type="ios-list-outline"></Icon>
                    <span>年级</span>
                </p>
                <ul>
                    <li v-for="item of gradeList" @click="changeGrade(item)" :class="{active:item.id==selGrade}">{{item.name}}</li>
                </ul>
            </div>
            <div v-if="selType ==2">
                <p>
                    <Icon type="ios-list-outline"></Icon>
                    <span>专题</span>
                </p>
                <ul>
                    <li v-for="item of specialList" @click="changeSpecial(item)" :class="{active:item.id==selSpecial}">{{item.name}}</li>
                </ul>
            </div>
            <div>
                <p>
                    <Icon type="ios-list-outline"></Icon>
                    <span>学科</span>
                </p>
                <ul>
                    <li v-for="item of subjectList" @click="changeSubject(item)" :class="{active:item.id==selSubject}">{{item.name}}</li>
                </ul>
            </div>
            
        </div>
       <div id="filter-content" class="w-1200">
     
            <div id="content-box">
                <ul class="filters" v-if="selType ==1">
                    <li v-for="item of titleList" :class="{active:item.id==localList}" @click="changelist(item)">
                        <span></span>{{item.name}}
                    </li>                                      
                </ul>
                <div class="contents" :class="{contentsAll:selType ==2}">
                    <div class="right-title">           
                        <div class="totel">共有 <span>30</span> 个资源</div>
                    </div>
                    <ul class="right-list">            
                        <li v-for="item of resourceList">
                        <div class="file-img">
                            <img src="/static/imgs/resource/fileXls.png" alt="文档图片">
                        </div>
                        <div class="file-content">
                            <h5>{{item.title}}</h5>
                            <p>
                            <span>大小：{{item.size}}</span>
                            <span>浏览：{{item.view}}</span>
                            <span>下载：{{item.downLoad}}次</span>
                            <span>收藏：{{item.collect}}</span>
                            </p>
                            <p>贡献者：{{item.creator}}</p>
                            <p>贡献时间：{{item.date}}</p>
                        </div>
                        <div class="file-star">
                            <Rate v-model="star"></Rate>
                        </div>
                        </li>                
                    </ul>
                    <Page :total="totalCount" show-elevator show-total class="page-box"></Page>	
                </div>
            </div>
        </div>
    </div>
       
</template>
<script>
export default {
  name:'SpecialClass',
  data(){
      return{
            typeList:[
                {id:1,name:'不限'},
                {id:2,name:'课件'},
                {id:3,name:'试卷'},
                {id:4,name:'学案'},
                {id:5,name:'教案'},
            ],
            type:1,
            star:5,
            totalCount:10,
            allType:[
                {id:1,name:'同步微课'},
                {id:2,name:'专题微课'}
            ],
            selType:1,
            periodList:[
                {id:1,name:'高中'},
                {id:2,name:'初中'},
                {id:3,name:'小学'},
            ],
            selPeriod:1,
            gradeList:[
                {id:0,name:'全部'},
                {id:1,name:'三年级'},
                {id:2,name:'四年级'},
                {id:3,name:'五年级'},
            ],
            selGrade:0,
            subjectList:[   
                {id:0,name:'全部'},             
                {id:1,name:'语文'},
                {id:2,name:'数学'},
                {id:3,name:'英语'},
                {id:4,name:'物理'},
                {id:5,name:'化学'},
                {id:6,name:'生物'},
                {id:7,name:'地理'},
                {id:8,name:'历史'},
                {id:9,name:'政治'}
            ],
            selSubject:0,
            specialList:[                
                {id:1,name:'奥数'},
                {id:2,name:'小升初'},
                {id:3,name:'中考'}
            ],
            selSpecial:1,
            titleList:[
                {id:1,name:'整式的加减'},             
                {id:2,name:'一元一次方程'},
                {id:3,name:'几何图形解析'},
                {id:4,name:'专题名称'},
            ],
            localList:1,
            resourceList:[
                {title:'高考快速提分秘籍',size:'7M',view:2400,downLoad:360,collect:20,creator:'张先生',date:'2018-3-26'},
                {title:'高考快速提分秘籍',size:'7M',view:2400,downLoad:360,collect:20,creator:'张先生',date:'2018-3-26'},
                {title:'高考快速提分秘籍',size:'7M',view:2400,downLoad:360,collect:20,creator:'张先生',date:'2018-3-26'},
                {title:'高考快速提分秘籍',size:'7M',view:2400,downLoad:360,collect:20,creator:'张先生',date:'2018-3-26'},
                {title:'高考快速提分秘籍',size:'7M',view:2400,downLoad:360,collect:20,creator:'张先生',date:'2018-3-26'}
            ]
      }
  },
  methods:{
    changeType(item){
      this.selType=item.id; 
    },
    changePeriod(item){
      this.selPeriod=item.id; 
    },
    changeGrade(item){
      this.selGrade=item.id; 
    },
    changeSubject(item){
      this.selSubject=item.id; 
    },
    changeSpecial(item){
      this.selSpecial=item.id; 
    },
    changelist(item){
      this.localList=item.id; 
    }
  }
}
</script>
<style scoped>
    #filter-list{
        margin-top: 60px;
        margin-bottom: 30px;
        padding-left: 20px;
    }
    #filter-list>div{
        overflow: hidden;
        margin-bottom: 20px;
    }
    #filter-list>div p{
        float: left;
        font-size: 14px;
        color: #999;
        padding: 8px 0;
    }
    #filter-list>div p span{
        margin-left: 35px;
    }
    #filter-list>div ul{
        float: left;
        margin-left: 60px;
    }
    #filter-list>div ul li{
        float: left;
        padding: 3px 15px;
        margin-right: 30px;
        font-size: 14px;
        color: #666;
        cursor: pointer;
    }
    #filter-list>div ul li.active{
        color: #fff;
        background-color: #1cb0ea;
    }   
   #filter-content{
      background-color: #fff; 
      margin-bottom: 80px;
      border:1px solid #e9e9e9;
   }
   #content-box{
     overflow: hidden;
     padding: 0 40px;
     width: 100%;
   }
   .filters{
     float: left;
     width: 240px;
     min-height: 650px;
     margin-top: 30px;
     padding-right: 20px;
     border-right:1px solid #eee;
   }
   .filters li{
     height: 60px;
     line-height: 60px;
     border-bottom: 1px solid #f3f3f3;
     font-size: 16px;
     padding-left: 20px;
   }   
   .filters li.active{
     height: 60px;
     line-height: 60px;
     border-bottom: 1px solid #f3f3f3;
     font-size: 20px;
     color: #1caaf1;
     position: relative;
   }
   .filters li.active span{
     position: absolute;
     left: 0;
     top: 15px;
     border-left: 3px solid #1caaf1;
     height: 30px;
   }
   .contents{
     float: left;
     width: 800px;
     margin-left: 40px;     
     margin-bottom:36px;
   }
   .contentsAll{
       width: 100%;
       margin-left: 0;
   }
   .right-title{     
     position: relative;     
     margin-top: 24px;
     height:40px;     
   }   
   .totel{
     position: absolute;
     right: 0;
     top: 10px;
     font-size: 14px;
   }
   .totel span{
     color: #1caaf1;
   }
   .right-list{
     padding: 0 20px 0 60px;
     border:1px solid #f3f3f3;
   }
   .right-list li{
     height: 180px;  
     padding-top: 40px;
     position: relative;   
     border-bottom:1px solid #f3f3f3;
   }
   .right-list li:last-child{     
     border-bottom:none;
   }
   .right-list li>div:last-child{
     position: absolute;
     right: 0;
     top: 30px;
   }
   .file-img{
     float: left;
   }
   .file-img img{
     width: 100px;
     height: 100px;
   }   
   .file-content{
     float: left;
     margin-left: 90px;
     font-size: 14px;
     color: #999;
   }
   .file-content p{
     margin: 5px 0;
   }
   .file-content p span{
     margin-right: 20px;
   }
   .file-content h5{
     color: #333;
     font-size: 14px;
   }
   .ivu-page{
     text-align: center;
     margin-top: 25px;
   }
   .file-star{
        text-align: right;
    }
</style>




