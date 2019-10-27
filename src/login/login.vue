<template>
    <div id="login" class="login">
      <el-col :span='24'>
        <video autoplay loop muted class="login-video">
          <source src="static/video/parking-bk.mp4" type="video/mp4"/>
        </video>
      </el-col>
      <el-row class="login-center">
        <el-col :span='16' :offset='4' class="login-title">
          <label>停车场车位资产管理云平台</label>
        </el-col>
      </el-row>
      <el-form :rules="rules" v-model="user">
        <el-row type="flex" justify="space-around">
          <el-col :span='6'>
          <el-form-item prop="userCode">
            <el-input placeholder="用户名" v-model="user.userCode" prefix-icon="el-icon-s-custom"></el-input>
          </el-form-item>
          </el-col>
        </el-row>
        <el-row type="flex" justify="space-around">
          <el-col :span='6'>
            <el-form-item prop="password">
              <el-input placeholder="密码" v-model="user.password" prefix-icon="el-icon-lock" show-password></el-input>
            </el-form-item>
          </el-col>
        </el-row>
        <el-row type="flex" justify="space-around">
          <el-col :span='6'>
            <el-button type="success" @click="dialogFormVisible = !dialogFormVisible">注册</el-button>
            <el-button type="primary" @click="login">登录</el-button>
          </el-col>
        </el-row>
      </el-form>
      <el-footer>
        <div class="footer">
          <span style="line-height: 60px;">Copyright ©2019      甜甜圈自主创业公司版权所有   京ICP备06007539号
              -31 京公网安备11010802031935号</span>
        </div>
      </el-footer>
      <el-dialog title="用户注册" v-if="dialogFormVisible">
        <Regist></Regist>
      </el-dialog>
    </div>
</template>

<script>
  import Regist from "./regist";
  export default {
    components: {Regist},
    name: "login",
    data(){
      return{
        dialogFormVisible: false,
        user:{
          userCode: '',
          password: ''
        },
        // 校验规则
        rules:{
          userCode:
            { required: true, //是否必填
              message: '用户名不能为空', //规则
              trigger: ['blur','change']  //何事件触发
            },
          password: [
            { required: true, //是否必填
              message: '密码不能为空', //规则
              trigger: ['blur','change']  //何事件触发
            },
            //可以设置双重验证标准
            { min: 8, max: 20,  message: '密码长度在8到20个字符', }
          ]
        }
      }
    },
    methods:{
      login(){
        if(!this.validate()){
          return
        }
        this.$message({
          message:'登录成功！欢迎您：'+this.user.usercode,
          type: 'success'
        });

      },
      validate(){
        let islogin = true
        if(this.user.usercode != 'txx'){
          islogin = !islogin
          this.$message({
            type: 'warning',
            message: '用户不存在！'
          })
        }else if(this.user.password != 'txx'){
          islogin = !islogin
          this.$message({
            type: 'warning',
            message: '密码错误，请重新输入！'
          })
        }
        return islogin
      }
    }
  }
</script>

<style scoped>
#login{
  width: 100%;
  height: 100%;
  margin-top: -60px;
}
.login-video{
  width: 100%;
  position: absolute;left: 0px;
  z-index: -1;
}
.login-center{
  width: 70%;
  height: 100%;
  margin: 60px auto auto auto;
  z-index: 99;
}
.login-title{
  padding-top: 6rem;
  padding-bottom: 4rem;
  font-size: 300%;
  font-weight: bold;
  color: rgba(115, 115, 115, 0.98);

}
  .el-button{
    width: 47.9%;
  }
  .footer{
    margin-top: 20rem;
    z-index: 99;
  }
.el-dialog{
  margin: auto;
  position: absolute;
  z-index: 999;
}
</style>
