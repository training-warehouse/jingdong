<template>
  <div class="wrapper">
    <img class="wrapper__img" src="http://www.dell-lee.com/imgs/vue3/user.png" alt="">
    <div class="wrapper__input">
      <input type="text" class="wrapper__input__content" placeholder="请输入用户名" v-model="username">
    </div>
    <div class="wrapper__input">
      <input type="password" class="wrapper__input__content" placeholder="请输入密码" v-model="password">
    </div>
    <div class="wrapper__login-button" @click="handleLogin">登录</div>
    <div class="wrapper__login-link" @click="handleRegister">立即注册</div>
    <Toast v-show="showToast" :message="toastMessage"/>
  </div>
</template>

<script>
import {reactive, toRefs} from 'vue'
import {useRouter} from 'vue-router'

import {post} from '@/utils/request'
import Toast, {useToastEffect} from '@/components/Toast'

const useLoginEffect = (router, toastShow) => {
  const data = reactive({
    username: '',
    password: ''
  })

  const handleLogin = async () => {
    if (!data.username || !data.password) {
      return toastShow('请填写用户名和密码')
    }

    try {
      const result = await post('/api/user/login', data)
      if (result?.errno === 0) {
        localStorage.isLogin = true
        await router.push({name: 'Home'})
      } else {
        toastShow(result.desc)
      }
    } catch (e) {
      toastShow('请求失败')
    }
  }

  const {username, password} = toRefs(data)
  return {handleLogin, username, password}
}

const useRegisterEffect = (router) => {
  const handleRegister = () => {
    router.push({name: 'Register'})
  }
  return {handleRegister}
}

export default {
  name: 'Login',
  components: {Toast},
  setup() {
    const router = useRouter()

    const {toastShow, showToast, toastMessage} = useToastEffect()
    const {handleLogin, username, password} = useLoginEffect(router, toastShow)
    const {handleRegister} = useRegisterEffect(router)

    return {handleLogin, handleRegister, username, password, showToast, toastMessage}
  }
}
</script>

<style scoped lang="scss">
@import "../../style/variables";

.wrapper {
  position: absolute;
  top: 50%;
  left: 0;
  right: 0;
  transform: translateY(-50%);

  &__img {
    display: block;
    margin: 0 auto .4rem auto;
    width: .66rem;
    height: .66rem;
  }

  &__input {
    height: .48rem;
    background: #F9F9F9;
    margin: 0 .4rem .16rem .4rem;
    border: 1px solid rgba(0, 0, 0, 0.1);
    border-radius: 6px;
    padding: 0 .16rem;
    box-sizing: border-box;

    &__content {
      border: none;
      outline: none;
      width: 100%;
      line-height: .48rem;
      background: none;
      font-size: .16rem;
      color: $content-notice-fontcolor;

      &::placeholder {
        color: $content-notice-fontcolor;
      }
    }
  }

  &__login-button {
    background: #0091FF;
    box-shadow: 0 .04rem .08rem 0 rgba(0, 145, 255, 0.32);
    border-radius: .04rem;
    color: #FFFFFF;
    margin: .32rem .4rem .16rem .4rem;
    line-height: .48rem;
    font-size: .16rem;
    text-align: center;
  }

  &__login-link {
    font-size: .14rem;
    color: $content-notice-fontcolor;
    text-align: center;
  }
}
</style>
