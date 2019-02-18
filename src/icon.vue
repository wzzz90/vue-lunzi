<template>
  <i :class="['iconfont', 'lunzi-icon', 'icon-'+name]"></i>
</template>

<script>
export default {
  name: 'Icon',
  props: ['name']
}

</script>
<style lang='scss' scoped>

    .lunzi-icon {
      font-size: 1em;
    }
</style>