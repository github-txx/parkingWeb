<template>
    <div class="regist">
      <el-form :rules="rules">
        <el-form-item prop="usercode">
          <el-input placeholder="用户名" v-model="user.usercode" prefix-icon="el-icon-s-custom"></el-input>
        </el-form-item>
        <el-form-item prop="username">
          <el-input placeholder="姓名" v-model="user.username" prefix-icon="el-icon-s-custom"></el-input>
        </el-form-item>
        <el-form-item prop="phonenum">
          <el-input placeholder="电话" v-model="user.phonenum" prefix-icon="el-icon-s-custom"></el-input>
        </el-form-item>
        <el-form-item prop="password">
          <el-input required placeholder="密码" v-model="user.password" prefix-icon="el-icon-lock" show-password></el-input>
        </el-form-item>
        <el-form-item prop="repassword">
          <el-input required placeholder="确认密码" v-model="repassword" prefix-icon="el-icon-lock" show-password></el-input>
        </el-form-item>
        <el-button type="success" @click="">注册</el-button>
        <el-button type="primary" @click="">重置</el-button>
      </el-form>
    </div>
</template>
<!--用户名、密码、姓名、电话、备注-->
<script>
  export default {
    name: 'regist',
    data(){
      return {
        repassword:'',
        user:{
          usercode:'',
          password:'',
          username:'',
          phonenum:'',
          note:''
        },
        // 校验规则
        rules:{
          usercode: [
            { required: true, //是否必填
              message: '请输入用户名', //规则
              trigger: 'blur'  //何事件触发
            }
          ],
          username: [
            { required: true, //是否必填
              message: '请输入姓名', //规则
              trigger: 'blur'  //何事件触发
            }
          ],
          password: [
            { required: true, //是否必填
              message: '请输入密码', //规则
              trigger: 'blur'  //何事件触发
            },
            //可以设置双重验证标准
            { min: 8, max: 20,  message: '密码长度为8到20个字母、数字、下划线组合'}
          ],
          repassword: [
            { required: true, //是否必填
              message: '请输入确认密码', //规则
              trigger: 'blur'  //何事件触发
            },
            //可以设置双重验证标准
            { value : user.password,  message: '密码长度在8到20个字母、数字、下划线组合'}
          ],
          phonenum: [
            { required: true, //是否必填
              message: '请输入电话', //规则
              trigger: 'blur'  //何事件触发
            },
            {
              true:/^1[0-9]{10}$/.test(value), message: '输入的电话号码格式有误！'
            }
          ],
        }
      }
    }
  }
</script>

<style scoped>

</style>
