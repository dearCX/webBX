<template>
    <div>
        <div class="register-content">
            <div class="common-title">
                <span>账号设置</span>
                <span class="active">填写个人信息</span>
            </div>
            <p>
                <span>性别：</span>
                 <RadioGroup v-model="gender">
                    <Radio label="男"></Radio>
                    <Radio label="女"></Radio>
                </RadioGroup>
            </p>
            <p>
                <span>年级：</span>
                <input type="text" placeholder="请输入年级">
            </p>
            <p>
                <span>民族：</span>
                <input type="text" placeholder="请输入民族">
            </p>
            <p>
                <span>身份证号：</span>
                <input type="text" placeholder="请输入身份证号">
            </p>
            <p>
                <span>出生日期：</span>
                <DatePicker type="date" placeholder="请选择出生日期" style="width: 400px" size="large"></DatePicker>
            </p>
            <p>
                <span>地址：</span> 
                <input type="text" placeholder="请输入地址">
            </p>
            <button type="button" id="next-btn" @click="toLogin">下一步</button>
        </div>
    </div>
</template>
<script>
export default {
    name:'StudentRegisterTwo',
    data(){
        return {
           gender:'男'           
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
        border:1px solid #dfe4e9;
        border-radius: 4px;
    }
    .register-content p.level select{
        width: 400px;
        height: 36px;
        line-height: 36px;
        padding-left: 10px;
        border:1px solid #dfe4e9;
        border-radius: 4px;
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
    }
    #next-btn{
        margin-left: 320px;
        width: 160px;
        height: 36px;
        line-height: 36px;
        background-color: #37b1ef;
        border-radius: 5px;
        color: #fff;
        text-align: center;
        border:none;
        font-size: 14px;
        cursor: pointer;
    }    
</style>


