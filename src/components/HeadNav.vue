<template>
    <section class="head-nav f-oh">
        <el-row>
            <el-col :span="6" class='logo-container'>
                <img src="../assets/logo.png" class='logo' alt="">
                <span class='title'>城驿通后台管理系统</span>
            </el-col>
            <el-col :span='6' class="user">
                <div class="userinfo">
                    <img src="../assets/images/portrait.png" class='avatar' alt="">
                    <div class='welcome'>
                        <p class='name comename'>欢迎</p>
                        <!--<p class='name avatarname'>{{ user_info.nickname }}</p>-->
                        <p class='name avatarname'>aa</p>
                    </div>
                    <span class='username'>
                        <el-dropdown trigger="click" @command='setDialogInfo'>
                            <span class="el-dropdown-link">
                                <i class="el-icon-caret-bottom el-icon--right"></i>
                            </span>
                            <el-dropdown-menu slot="dropdown">
                                <el-dropdown-item command='info'>个人信息</el-dropdown-item>
                                <el-dropdown-item  command='logout'>退出</el-dropdown-item>
                            </el-dropdown-menu>
                        </el-dropdown>
                     </span>
                </div>
            </el-col>

        </el-row>

    </section>
</template>
<script>
export default {
    name: "head-nav",

    data () {
        return {
            user_info: {},
        }
    },
    computed: {
        user() {
            // return this.$store.getters.user;
        }
    },
    methods: {
        getUser () {
            // this.axios.post('/api/admin/user/login', qs.stringify({phone:15988831425,password:123456})).then((res) => {
            //     this.user_info = res.data.data;
            //     console.log(this.user_info)
            // }).catch((err) => {
            //
            // });
        },
        setDialogInfo(cmditem) {
          // if (!cmditem) {
          //   console.log("test");
          //   this.$message("菜单选项缺少command属性");
          //   return;
          // }
          switch (cmditem) {
            case "info":
              this.showInfoList();
              break;
            case "logout":
              this.logout();
              break;
          }
        },
        // 个人信息
        showInfoList() {
          this.$router.push("/infoshow");
        },
        // 退出
        logout() {
          // 清除token
          // localStorage.removeItem("eleToken");
          // this.$store.dispatch("clearCurrentState");

          // 页面跳转
          this.$router.push("/login");
        }
    },
    created (){
        this.getUser();
    }
};
</script>

<style scoped>
.head-nav {
    background: #324057;
    color: #fff;
}

.logo-container {
  line-height: 60px;
  min-width: 400px;
}

.logo {
  height: 50px;
  width: 50px;
  margin-right: 5px;
  vertical-align: middle;
  display: inline-block;
}

.title {
  vertical-align: middle;
  font-size: 22px;
  /*font-family: "Microsoft YaHei";*/
  letter-spacing: 3px;
  color: #fff;
}

.user {
  line-height: 60px;
  text-align: right;
  float: right;
  padding-right: 10px;
}

.avatar {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  vertical-align: middle;
  display: inline-block;
}

.welcome {
  display: inline-block;
  width: auto;
  vertical-align: middle;
  padding: 0 5px;
}

.name {
  line-height: 20px;
  text-align: center;
  font-size: 14px;
}

.comename {
  font-size: 12px;
}

.avatarname {
  color: #409eff;
  font-weight: bolder;
}

.username {
  cursor: pointer;
  margin-right: 5px;
}
</style>
