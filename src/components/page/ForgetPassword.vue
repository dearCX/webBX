<template>
    <div id="register">
            <div id="header-container">
                <div id="header" class="w-1200">    
                    <div class="left">
                        <div class="logo">
                            <img src="../../assets/imgs/index/u124.png" alt="这是logo图片">
                        </div>        
                        <div class="title">
                            <div>伴学网教育云平台</div>
                            <p>专注中小学个性化教育</p>
                        </div>
                        <h2 class="find-password">找回密码</h2>
                    </div> 
                </div>
            </div> 
            <section id="section" class="w-1200">
                <p class="find-password-title">
                    <span>找回密码</span>
                </p>    
                <div class="register-content">                   
                    <p>
                        <span>手机号码：</span>
                        <input type="text" placeholder="请输入手机号">
                    </p>
                    <p class="msg-btn">
                        <span>短信验证码：</span>
                        <input type="text" placeholder="请输入短信验证码">
                        <button type="button">发送验证码</button>
                    </p>
                    <p>
                        <span>新密码：</span>
                        <input type="password" placeholder="请输入新密码">
                    </p>
                    <p>
                        <span>确认新密码：</span>
                        <input type="password" placeholder="请再次输入新密码">
                    </p>
                    <button type="button" id="next-btn" @click="toLogin">确认</button>
                </div>           
            </section>
            <v-foot></v-foot>
    </div>
</template>
<script>
import vFoot from '@/components/common/Footer'; 
export default {
    name:'ForgetPassword',
    components:{
        vFoot
    },
    data(){
        return {
           
        }
    },
    methods:{
        toLogin(){
            this.$router.push({
                path:'/Login'
            });
        }
    }
}
</script>
<style scoped>    
    #header-container{
    width: 100%;
    background-color: #fff;
    }
    #header{  
    height:120px;
    margin: auto;  
    overflow: hidden;
    padding-top: 34px; 
    }
    #header>div.left{
    overflow: hidden;  
    height: 53px;
    }
    #header>.left>div{
    float: left;
    }
    .logo{
    margin-right: 10px;
    }
    .logo img{
    height: 53px;
    }
    .title{
    text-align: center;
    padding-right: 25px;
    }
    .title div{
    font-family: FZZXHJW--GB1-0;
        font-size: 20px;
        color: #333;
    }
    .title p{  
        font-family: MicrosoftYaHei;
        font-size: 14px;	
        color: #999;
    }
    .find-password{
        float: left;
        height: 40px;
        padding-left: 20px;
        margin-left: 55px;
        margin-top: 10px;
        font-weight: normal;
        border-left:1px solid #e9e9e9;
        font-size: 20px;
        color: #666;
    }
    #section{
    min-height: 600px;
    padding: 40px 130px;
    margin-top: 40px;
    margin-bottom: 80px;
    background-color: #fff;
    border:1px solid #dfe4e9;
    }
    .find-password-title{
        height: 40px;
        margin-bottom: 40px;
        border-bottom:1px solid #dfe4e9;
        font-size: 20px;
        color: #666;
    }
    .find-password-title span{  
        display: inline-block;
        padding-bottom: 9px;      
        margin-right: 40px;
        cursor: pointer;
    }    
    .common-title{
        height: 50px;
        margin-bottom: 38px;
        padding-top: 14px;
        text-align: center;
        background: url('../../assets/imgs/register/registerStep.png') no-repeat center top;
    }
    .common-title span{
        margin-right: 60px;
        margin-left: 80px;
        font-size: 16px;
        color: #666;
    }
    .common-title span.active{
        color: #37b1ef;
    }
    .register-content p{
        width: 520px;
        margin: auto;
        margin-bottom: 30px;
    }
    .register-content p span{
        display: inline-block;
        width: 90px;
        margin-right: 20px;
        text-align: right;
        color: #7b8085;
        font-size: 14px;
    }
    .register-content p input{
        width: 400px;
        height: 36px;
        line-height: 36px;
        padding-left: 10px;
        border-radius: 4px;
        border:1px solid #dfe4e9;
    }   
    .register-content p.msg-btn input{
        width: 290px;
        margin-right: 5px;
    }    
    .msg-btn button{
        width: 100px;
        height: 36px;
        line-height: 36px;
        text-align: center;
        color: #f8f8f8;
        border:none;
        background-color: #b7b7b7;
        cursor: pointer;
        border-radius: 4px;
    }
    #next-btn{
        margin-left: 320px;
        width: 160px;
        height: 40px;
        line-height: 40px;
        background-color: #37b1ef;
        border-radius: 5px;
        color: #fff;
        text-align: center;
        border:none;
        font-size: 14px;
        cursor: pointer;
    }
</style>


