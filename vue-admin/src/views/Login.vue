<template>
  <div class="bg">
    <div class="login">
      <h3>登录</h3>
      <div class="Input">
        <el-input v-model="name" placeholder="用户名"></el-input>
      </div>
      <div class="Input">
        <el-input v-model="pass" placeholder="密码"></el-input>
      </div>
      <div class="Input">
        <el-button type="primary">登录</el-button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Login",
  data() {
    return {
      // bg: require("../assets/bg.jpg"),
      name: "",
      pass: "",
    };
  },
};
</script>

<style lang="less">
.bg {
  width: 100%;
  height: 100%;
  background: url("../assets/bg.jpg") left top no-repeat;
  position: fixed;
  left: 0;
  top: 0;
  right: 0;
  bottom: 0;
  .login{
    width:400px;
    height:300px;
    padding:20px;
    border-radius: 10px;
    background: rgba(255,255,255,0.8);
    position: absolute;
    left:50%;
    top:50%;
    transform: translate(-50%, -50%);
    h3 {
      font-size: 30px;
      color:#000000;
      text-align: center;
      margin-bottom:30px;
    }
    .Input{
      margin-bottom:20px;
      button{
        width:100%;
      }
    }
  }
}
</style>