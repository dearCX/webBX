<template>
    <div>
        <div class="register-content">
            <div class="common-title">
                <span class="active">账号设置</span>
                <span>填写个人信息</span>
            </div>
            <p>
                <span>手机号码：</span>
                <input type="text" placeholder="请输入手机号">
            </p>
            <p class="verify-btn">
                <span>验证码：</span>
                <input type="text" placeholder="请输入验证码">
                <button type="button">SNVK</button>
            </p>
            <p class="msg-btn">
                <span>短信验证码：</span>
                <input type="text" placeholder="请输入短信验证码">
                <button type="button">发送验证码</button>
            </p>
            <p>
                <span>密码：</span>
                <input type="password" placeholder="请输入密码">
            </p>
            <button type="button" id="next-btn" @click="toTeacherRegisterTwo">下一步</button>
        </div>
    </div>
</template>
<script>
export default {
    name:'TeacherRegisterOne',
    data(){
        return {
           
        }
    },
    methods:{
        toTeacherRegisterTwo(){
            this.$router.push({
                path:'/Register/TeacherRegisterTwo',
                query:{}
            });
        }
    }
}
</script>
<style scoped>    
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
    .register-content p.verify-btn input,
    .register-content p.msg-btn input{
        width: 290px;
        margin-right: 5px;
    }
    .verify-btn button{
        width: 100px;
        height: 36px;
        line-height: 36px;
        text-align: center;
        color: #fff;
        border:none;
        background-color: #37b1ef;
        cursor: pointer;
        border-radius: 4px;
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


