<template>
  <div class="wrapper">
    <StaticPart></StaticPart>
    <Nearby></Nearby>
  </div>
  <Docker></Docker>
</template>

<script>
import StaticPart from '@/views/home/StaticPart'
import Nearby from '@/views/home/Nearby'
import Docker from '@/views/home/Docker'

export default {
  name: 'Home',
  components: {
    StaticPart,
    Nearby,
    Docker
  }
}
</script>

<style lang="scss" scoped>
.wrapper {
  position: absolute;
  left: 0;
  top: 0;
  bottom: 0.5rem;
  right: 0;
  padding: 0 0.18rem 0.1rem 0.18rem;
  overflow-y: auto;
}
</style>
