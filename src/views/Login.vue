<template>
    <div>
        <el-form :rules="loginRules" ref="loginForm" :model="loginForm" class="loginContainer">
            <h3 class="loginTitle">系统登陆</h3>
            <el-form-item prop="username">
                <el-input type="text" v-model="loginForm.username" placeholder="请输入用户名"></el-input>
            </el-form-item>
            <el-form-item prop="password">
                <el-input v-model="loginForm.password" auto-complete="false" placeholder="请输入密码"></el-input>
            </el-form-item>
            <el-form-item prop="code">
                <el-input type="text" auto-complete="false" v-model="loginForm.code" placeholder="点击图片更换验证码" style="width:250px;margin-right: 5px"></el-input>
                <img :src="loginForm.captureUrl">
            </el-form-item>
            <el-checkbox v-model="loginForm.checked" class="loginRemeberme">记住我</el-checkbox>
            <el-button type="primary" style="width: 100%" @click="submitLogin">登录</el-button>
        </el-form>
    </div>
</template>

<script>
    export default {
        name:"Login",
        data(){
            return{
                loginForm:{
                    captureUrl:'',
                    username:'admin',
                    password:'123',
                    code:'',
                    checked:true,
                },
                loginRules:{
                    username: [{required:true,message:'请输入用户名',trigger:'blur'}], //与prop里的username对应上
                    password: [{required:true,message:'请输入密码',trigger:'blur'}],
                    code: [{required:true,message:'请输入验证码',trigger:'blur'}]
                }
            }
        },
        methods:{
            submitLogin(){
                this.$refs.loginForm.validate((valid) => {
                    if (valid) {
                        alert('submit!');
                    } else {
                        this.$message.error('请输入所有字段！');
                        return false;
                    }
                });
            }
        }
    }
</script>

<style scoped>
    .loginContainer{
        border-radius: 15px;
        background-clip: padding-box;
        margin: 180px auto;
        width:350px;
        padding: 45px 35px 20px 35px;
        background: #fff;
        border: 1px solid #eaeaea;
        box-shadow: 0 0 25px #cac6c6;
    }
    .loginTitle{
        margin: 0px auto 35px auto;
        text-align: center;
    }
    .loginRemeberme{
        text-align: left;
        margin: 0px 0px 20px 0px;
    }
</style>