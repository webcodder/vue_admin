<template>
    <div class="login">
        <section class="form_container">
            <div class="manage_tip">
                <span class="title">城驿通后台管理系统</span>
            </div>
            <el-form :model="loginUser" status-icon :rules="rules" ref="loginForm" class="loginForm" label-width="80px">
                <el-form-item label="手机" prop="phone">
                    <el-input v-model="loginUser.phone" placeholder="请输入用户名"></el-input>
                </el-form-item>
                <el-form-item label="密码" prop="password">
                    <el-input v-model="loginUser.password" placeholder="请输入密码" type="password"></el-input>
                </el-form-item>
                <el-form-item>
                    <el-button type="primary" @click="submitForm('loginForm')" @keyup.enter.native="submitForm('registerForm')" class="submit_btn">登  录</el-button>
                </el-form-item>
                <div class="tiparea">
                    <p>还没有账号？现在<router-link to='/register'>注册</router-link></p>
                </div>
            </el-form>
        </section>
    </div>
</template>

<script>


export default {
  name: "login",

  data() {
    return {
      loginUser: {
        phone: "",
        password: ""
      },
      rules: {
          phone: [
              { required: true, message: "用户名不能为空", trigger: "blur" },
              { min: 2, max: 30, message: "长度在 2 到 30 个字符", trigger: "blur" }
          ],
        password: [
          { required: true, message: "密码不能为空", trigger: "blur" },
          { min: 6, max: 30, message: "长度在 6 到 30 个字符", trigger: "blur" }
        ]
      }
    };
  },

  methods: {
    submitForm(formName) {
      this.$refs[formName].validate(valid => {
        if (valid) {
          this.axios.post("/api/admin/user/login", qs.stringify(this.loginUser)).then(res => {
            console.log(res);
          });
        } else {
          console.log("error submit!!");
          return false;
        }
      });
    },
    // isEmpty(value) {
    //   return (
    //     value === undefined ||
    //     value === null ||
    //     (typeof value === "object" && Object.keys(value).length === 0) ||
    //     (typeof value === "string" && value.trim().length === 0)
    //   );
    // }
  },
    //预处理数据
    created: function(){
        //console.log($('body'));
    },
};
</script>

<style scoped>
.login {
  position: absolute;
  width: 100%;
  height: 100%;
  background: url(../assets/images/bg.jpg) no-repeat center center;
  background-size: 100% 100%;
}
.form_container {
  width: 370px;
  height: 210px;
  position: absolute;
  top: 20%;
  left: 34%;
  padding: 25px;
  border-radius: 5px;
  text-align: center;
}
.form_container .manage_tip .title {
  /*font-family: "Microsoft YaHei";*/
  font-weight: bold;
  font-size: 26px;
  color: #fff;
}
.loginForm {
  margin-top: 20px;
  background-color: #fff;
  padding: 20px 40px 20px 20px;
  border-radius: 5px;
  box-shadow: 0 5px 10px #cccc;
}

.submit_btn {
  width: 100%;
}

.tiparea {
  text-align: right;
  font-size: 12px;
  color: #333;
}

.tiparea p a {
  color: #409eff;
}
</style>


