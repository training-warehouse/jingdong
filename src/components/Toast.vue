<template>
  <div class="toast">{{ message }}</div>
</template>

<script>

import {reactive, toRefs} from 'vue'

export const useToastEffect = () => {
  const toastData = reactive({
    showToast: false,
    toastMessage: ''
  })

  const toastShow = (msg) => {
    toastData.toastMessage = msg
    toastData.showToast = true
    setTimeout(() => {
      toastData.showToast = false
      toastData.toastMessage = ''
    }, 2000)
  }

  const {showToast, toastMessage} = toRefs(toastData)

  return {toastShow, showToast, toastMessage}
}

export default {
  name: 'Toast',
  props: ['message']
}
</script>

<style lang="scss" scoped>
.toast {
  position: fixed;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  padding: .1rem;
  background: rgba(0, 0, 0, .35);
  border-radius: .05rem;
  color: #FFFFFF;
}
</style>
