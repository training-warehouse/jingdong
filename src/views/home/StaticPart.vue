<template>
  <div class="position">
    <span class="iconfont position__icon">&#xe61f;</span>
    北京理工大学
    <span class="iconfont position__notice">&#xe7c4;</span>
  </div>
  <div class="search">
    <span class="iconfont">&#xe741;</span>
    <span class="search__text">山姆会员商店优惠商品</span>
  </div>
  <div class="banner">
    <img class="banner__img" src="http://www.dell-lee.com/imgs/vue3/banner.jpg" alt="">
  </div>
  <div class="icons">
    <div class="icons__item" v-for="(icon,index) in iconsList" :key="index">
      <img class="icons__item__img" :src="icon.imgUrl" alt="">
      <p class="icons__item__desc">{{icon.title}}</p>
    </div>
  </div>
  <div class="gap"></div>
</template>

<script>
export default {
  name: 'StaticPart',
  setup() {
    const iconsList = [{
      imgUrl: 'http://www.dell-lee.com/imgs/vue3/超市.png',
      title: '超市便利'
    }, {
      imgUrl: 'http://www.dell-lee.com/imgs/vue3/超市.png',
      title: '超市便利'
    }, {
      imgUrl: 'http://www.dell-lee.com/imgs/vue3/超市.png',
      title: '超市便利'
    }, {
      imgUrl: 'http://www.dell-lee.com/imgs/vue3/超市.png',
      title: '超市便利'
    }, {
      imgUrl: 'http://www.dell-lee.com/imgs/vue3/超市.png',
      title: '超市便利'
    }, {
      imgUrl: 'http://www.dell-lee.com/imgs/vue3/超市.png',
      title: '超市便利'
    }, {
      imgUrl: 'http://www.dell-lee.com/imgs/vue3/超市.png',
      title: '超市便利'
    }, {
      imgUrl: 'http://www.dell-lee.com/imgs/vue3/超市.png',
      title: '超市便利'
    }, {
      imgUrl: 'http://www.dell-lee.com/imgs/vue3/超市.png',
      title: '超市便利'
    }, {
      imgUrl: 'http://www.dell-lee.com/imgs/vue3/超市.png',
      title: '超市便利'
    }]
    return {
      iconsList
    }
  }
}
</script>

<style lang="scss" scoped>
@import "../../style/variables.scss";
@import "../../style/mixins.scss";

.position {
  position: relative;
  padding: 0.16rem 0.24rem 0.16rem 0;
  line-height: 0.22rem;
  font-size: 0.16rem;
  color: $content-fontcolor;
  @include ellipsis;

  .position__icon {
    position: relative;
    top: 0.01rem;
    font-size: 0.2rem;
  }

  .position__notice {
    position: absolute;
    font-size: 0.2rem;
    right: 0;
    top: 0.17rem;
  }
}

.search {
  margin-bottom: 0.12rem;
  line-height: 0.32rem;
  background: #F5F5F5;
  color: #B7B7B7;
  border-radius: 0.16rem;

  .iconfont {
    position: relative;
    font-size: 0.2rem;
    top: 0.03rem;
    display: inline-block;
    padding: 0 0.08rem 0 0.16rem;
  }

  &__text {
    display: inline-block;
    font-size: 0.14rem;
  }
}

.banner {
  height: 0;
  overflow: hidden;
  padding-bottom: 25.4%; // 避免图片下方区域抖动
  &__img {
    width: 100%;
  }
}

.icons {
  display: flex;
  flex-wrap: wrap;
  margin-top: 0.16rem;

  &__item {
    width: 20%;

    &__img {
      display: block;
      width: 0.4rem;
      height: 0.4rem;
      margin: 0 auto;
    }

    &__desc {
      text-align: center;
      margin: 0.06rem 0 0.16rem 0;
      color: $content-fontcolor;
    }
  }
}

</style>
