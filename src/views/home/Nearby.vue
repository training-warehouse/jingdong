<template>
  <div class="nearby">
    <h3 class="nearby__title">附近店铺</h3>
    <div class="nearby__item" v-for="item in nearbyList" :key="item.id">
      <img :src="item.imgUrl" alt="" class="nearby__item__img">
      <div class="nearby__content">
        <div class="nearby__content__title">{{ item.title }}</div>
        <div class="nearby__content__tags">
          <span class="nearby__content__tag" v-for="(tag,index) in item.tags" :key="index">{{ tag }}</span>
        </div>
        <div class="nearby__content__highlight">{{ item.desc }}</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Nearby',
  setup() {
    const nearbyList = [{
      id: 1,
      title: '沃尔玛',
      tags: ['月售1万+', '起送￥0', '基础运费￥5'],
      desc: 'VIP尊享满89元减4元运费券（每月3张）',
      imgUrl: 'http://www.dell-lee.com/imgs/vue3/near.png'
    }, {
      id: 2,
      title: '沃尔玛',
      tags: ['月售1万+', '起送￥0', '基础运费￥5'],
      desc: 'VIP尊享满89元减4元运费券（每月3张）',
      imgUrl: 'http://www.dell-lee.com/imgs/vue3/near.png'
    }, {
      id: 3,
      title: '沃尔玛',
      tags: ['月售1万+', '起送￥0', '基础运费￥5'],
      desc: 'VIP尊享满89元减4元运费券（每月3张）',
      imgUrl: 'http://www.dell-lee.com/imgs/vue3/near.png'
    }]
    return {
      nearbyList
    }
  }
}
</script>

<style lang="scss" scoped>
@import "../../style/variables.scss";

.nearby {
  &__title {
    margin: 0.16rem 0 0.02rem 0;
    font-size: 0.18rem;
    font-weight: normal;
    color: $content-fontcolor;
  }

  &__item {
    display: flex;
    padding-top: .12rem;

    &__img {
      margin-right: 0.16rem;
      width: 0.56rem;
      height: 0.56rem;
    }
  }

  &__content {
    flex: 1;
    border-bottom: 0.01rem solid $content-bgColor;
    padding-bottom: 0.12rem;

    &__title {
      line-height: .22rem;
      font-size: .16rem;
      color: $content-fontcolor;
    }

    &__tags {
      line-height: .18rem;
      font-size: .13rem;
      color: $content-fontcolor;
      margin-top: .08rem;
    }

    &__tag {
      margin-right: .16rem;
    }

    &__highlight {
      line-height: .18rem;
      font-size: .13rem;
      color: #E93B3B;
      margin: .08rem 0 0 0;
    }
  }
}
</style>
