<template>
  <div class="login-container">
    <div class="layer">
      <div class="some-space">
        <div class="form">
          <h2>轴承匹配系统</h2>
          <div class="item">
            <i class="iconfont icon-user"></i>
            <input
              autocomplete="off"
              type="text"
              class="input"
              v-model="userName"
              placeholder="请输入用户名"
            />
          </div>
          <div class="item">
            <i class="iconfont icon-password"></i>
            <input
              autocomplete="off"
              type="password"
              class="input"
              v-model="userPwd"
              maxlength="20"
              @keyup.enter="login"
              placeholder="请输入密码"
            />
          </div>
          <button class="loginBtn" :disabled="isLoginAble" @click.stop="login">
            立即登录
          </button>
          <div class="tip">
            默认用户名：admin ，默认密码：123456
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { ref, computed } from 'vue'
import { useRouter } from 'vue-router'

export default {
  name: 'Login',
  components: {},
  setup() {
    const userName = ref('admin')
    const userPwd = ref('123456')
    const router = useRouter()

    const isLoginAble = computed(() => {
      return !(userName.value && userPwd.value)
    })

    const login = () => {
      if (userName.value === 'admin' && userPwd.value === '123456') {
        // 登录成功，跳转到homepage页面
        router.push('/homepage')
      } else {
        // 显示错误提示
        console.log('请输入正确的用户名和密码')
      }
    }

    return {
      userName,
      userPwd,
      isLoginAble,
      login
    }
  }
}
</script>

<style lang="scss" scoped>
.login-container {
  .layer {
    position: absolute;
    height: 100%;
    width: 100%;
    background: #013567;
  }
  .some-space {
    color: white;
    font-weight: 100;
    letter-spacing: 2px;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    z-index: 1001;

    .form {
      width: 460px;
      height: auto;
      background: rgba(75, 139, 247, 0.05);
      margin: 0 auto;
      padding: 35px 30px 25px;
      box-shadow: 1px 1px 16px #7ccef4 inset;
      border-radius: 10px;
      .item {
        display: flex;
        align-items: center;
        margin-bottom: 25px;
        border-bottom: 1px solid #d3d7f7;
        i {
          color: #d3d7f7;
          margin-right: 10px;
        }
      }
      h2 {
        text-align: center;
        font-weight: normal;
        font-size: 26px;
        color: #d3d7f7;
        padding-bottom: 35px;
      }
      .input {
        font-size: 16px;
        line-height: 30px;
        width: 100%;
        color: #d3d7f7;
        outline: none;
        border: none;
        background-color: rgba(0, 0, 0, 0);
        padding: 10px 0;
      }
      .loginBtn {
        width: 100%;
        padding: 12px 0;
        border: 1px solid #d3d7f7;
        font-size: 16px;
        color: #d3d7f7;
        cursor: pointer;
        background: transparent;
        border-radius: 4px;
        margin-top: 10px;
        &:hover {
          color: #fff;
        }
      }
      .tip {
        font-size: 12px;
        padding-top: 20px;
      }
    }
  }
}
</style>
