<template>
  <div class="docker">
    <span class="docker__item" v-for="(item,index) in dockerList" :key="item.title"
          :class="currentIndex === index?'docker__item--active':''">
    <div class="iconfont" v-html="item.icon"></div>
    <div class="docker__title">{{ item.title }}</div>
    </span>
  </div>
</template>

<script>
export default {
  name: 'Docker',
  setup () {
    const currentIndex = 0
    const dockerList = [
      {
        icon: '&#xe7d8;',
        title: '首页'
      },
      {
        icon: '&#xeb4a;',
        title: '购物车'
      },
      {
        icon: '&#xe713;',
        title: '订单'
      },
      {
        icon: '&#xe660;',
        title: '我的'
      }
    ]
    return {
      currentIndex,
      dockerList
    }
  }
}
</script>

<style lang="scss" scoped>
@import "../../style/variables.scss";

.docker {
  display: flex;
  position: absolute;
  padding: 0 0.18rem;
  box-sizing: border-box;
  left: 0;
  bottom: 0;
  width: 100%;
  height: 0.49rem;
  border-top: 0.01rem solid $content-bgColor;
  color: $content-fontcolor;

  &__item {
    flex: 1;
    text-align: center;

    .iconfont {
      font-size: 0.18rem;
      margin: 0.07rem 0 0.02rem 0;
    }

    .docker__title {
      font-size: 0.2rem;
      transform: scale(0.5, 0.5);
      transform-origin: center top;
    }

    &--active {
      color: #1FA4FC;
    }
  }
}
</style>
