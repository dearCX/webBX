<template>
  <div id="filter-content" class="w-1200">     
      <div id="content-box">
        <div class="filters">
          <div>筛选条件</div>
        </div>
        <div class="contents">
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
</template>
<script>
export default {
  name:'HightQualityClass',
  data(){
      return{ 
          star:5,
          totalCount:10,
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
   
  }
}
</script>
<style scoped>
   #filter-content{
      background-color: #fff;      
      margin-top: 40px;
      margin-bottom: 80px;
      border:1px solid #e9e9e9;
   }   
   #content-box{
     overflow: hidden;
     padding: 0 60px 0 40px;
     width: 100%;
   }
   .filters{
     float: left;
     width: 240px;
     border-right:1px solid #dfe4e9;
   }
   .contents{
     float: left;
     width: 800px;
     margin-left: 40px;     
     margin-bottom:36px;
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


