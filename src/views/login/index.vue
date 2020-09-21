<template>
  <div class="login-container">
    <el-form ref="loginForm" v-model="loginForm" :rules="loginRules" class="login-form" autocomplete="on"
      label-position="left">
      <div class="title-container">
        <h3 class="title">Login Form</h3>
      </div>
      <el-form-item prop="username">
        <span class="svg-container">
        </span>
      </el-form-item>
    </el-form>
  </div>
</template>

<script>
export default {
  name: 'Login',
  data() {
    const validateUser  = (rule, value, callback) => {
      if (!validateUser(value)) {
        callback(new Error('Please enter the correct user name'))
      } else {
        callback()
      }
    }
    const validatePwd = (rule, value, callback) => {
      if (value.length < 4) {
        callback(new Error('The password can not be less than 6 digits'))
      } else {
        callback()
      }
    }
    return {
      loginForm: {
        user: 'admin',
        pwd: '111111'
      },
      loginRules: {
        user: [{ required: true, trigger: 'blur', validator: validateUser}],
        pwd: [{ required: true, trigger: 'blur', validator: validatePwd}]
      }
    }
  }
}
</script>