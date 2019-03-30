<template>
  <div class="login">
    <el-form
      :model="ruleForm"
      :rules="rules"
      ref="ruleForm"
      label-width="100px"
      class="demo-ruleForm"
      label-position="left"
    >
      <el-form-item label="用户账号" prop="username">
        <el-input v-model="ruleForm.username" placeholder="请输入账号"></el-input>
      </el-form-item>
      <el-form-item label="密码" prop="password">
        <el-input v-model="ruleForm.password" placeholder="请输入密码"></el-input>
      </el-form-item>
      <el-form-item class="bottom">
        <el-button type="primary" @click="login">登录</el-button>
        <el-button @click="resetForm('ruleForm')" class="btn">重置</el-button>
      </el-form-item>
    </el-form>
  </div>
</template>

<script>
export default {
  data () {
    return {
      ruleForm: {
        username: '',
        password: ''
      },
      rules: {
        username: [
          { required: true, message: '请输入账号', trigger: 'blur' },
          { min: 3, max: 10, message: '长度在 3到 10个字符', trigger: 'blur' }
        ],
        password: [
          { required: true, message: '请输入活动名称', trigger: 'blur' },
          { min: 4, max: 8, message: '长度在 4到 8个字符', trigger: 'blur' }
        ]
      }
    }
  },
  methods: {
    async login () {
      let res = await this.$axios.post('/login', this.ruleForm)
      console.log(res)
      if (res.status === 200) {
        console.log('登录成功')
        this.$router.push('/home')
      }
    },
    resetForm (formName) {
      this.$refs[formName].resetFields()
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less">
.login {
  width: 450px;
  height: 200px;
  margin: 150px auto;
  border: 1px solid #eee;
  border-radius: 10px;
  padding: 30px;
  background-color: #fff;
  .bottom {
    margin-top: 40px;
    .btn {
      margin-left: 100px;
    }
  }
}
</style>
