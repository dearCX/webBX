<template>
    <div>
        <ul class="classes-content">
            <li v-for="item in classList" @click="goToInfo(item.id)">
                <div class="classes-img" v-show="item.imgUrl!=''">
                    <img :src="item.imgUrl" alt="课程图片">
                    <p></p>
                </div>                
                <div class="class-price" v-show="item.imgUrl!=''">
                    <p>{{item.name}}</p>
                    <span>￥</span>
                    <b>{{(item.money)/100}}</b>
                </div> 
                <div class="classText" v-show="item.imgUrl==''">
                    <h1>{{item.name}}</h1>
                    <p>{{item.gradeName+item.subjectName+item.versionName}}</p>
                    <p>
                        <span>共{{item.videoNums}}讲</span>
                        <span v-show="item.isFree==0">￥<b>{{(item.money)/100}}</b></span>
                        <span v-show="item.isFree==1" class="free">免费</span>
                    </p>
                </div>               
            </li>           
        </ul>
    </div>
</template>
<script>
export default {
    name:'ClassList',
    data(){
        return {

        }
    },
    props:{
        classList:{
            type:Array,
            required:true
        }
    },
    methods:{
        goToInfo(id){
            this.$router.push('/ClassDatile?courseId='+id);
        }
    }  
}
</script>
<style scoped>
    .classes-content{        
        width: 100%;
        display: -webkit-flex; 
        display: flex;
        flex-direction: row ; 
        flex-wrap: wrap;
        justify-content: space-between;
    }
    .classes-content li{      
        width: 260px;
        margin-bottom: 20px;        
    }
    .classes-content li:hover .classes-img p{      
        display: block;  
    }
    .classes-content li:hover{      
        position: relative;
        top: -10px;
    }
    .classes-img{
        width: 260px;
        height: 195px;
        position: relative;
    }    
    .classes-img img{
        width: 100%;        
	    height: 100%;        
    }
    .classes-img p{
        position: absolute;
        top: 0;
        left: 0;        
        width: 100%;        
        height: 100%;
        background-color:rgba(0,0,0,.3);
        display: none;
    }
    .class-price{        
        text-align: center;
        width: 260px;
        height: 70px;
        box-shadow: 0px 5px 7px 0px rgba(70,130,147,.2);
    }
    .class-price p{   
        padding-top: 15px;     
        font-size: 16px;        
        color: #666;
    }
    .class-price span{           
        font-size:14px;        
        color: #666;
    }
    .class-price b,.classText b,.free{           
        font-size:20px;        
        color: #ff4242;
    }  
    .classText{
        width: 260px;
        height: 265px;
        background-color: #eee;
    }  
    .classText{

    }
</style>


