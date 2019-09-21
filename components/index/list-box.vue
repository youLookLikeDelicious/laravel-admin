<!--props数据结构
resource:
{
  header: '',
  list: []
}-->
<template>
  <ul class="list-box">
      <li>{{resource.header}}</li>
      <li v-for="(item, index) in resource.list" :key="index"  v-bind:style="{ textIndent: (( item.split('/').length || 1) - 1) * 2 + 'em' }" :class="{'directory-prefix': item.indexOf('.php') === -1}">
          {{ item.split('/').pop() }}
      </li>
  </ul>
</template>

<script>
export default {
  name: 'list-box',
  props: {
    resource: Object
  },
  data () {
    return {
      spaceChar: ' '
    }
  }
}
</script>

<style lang="scss">
    .list-box{
        list-style: none;
        width: 86%;
        border-top-left-radius: .3rem;
        background-color: #fff;
        border-top-left-radius: .3rem;
        border-top-right-radius: 1.5rem;
        overflow: hidden;
        li{
            padding: .3rem .5rem;
            -webkit-box-sizing: border-box;
            -moz-box-sizing: border-box;
            box-sizing: border-box;
            border-bottom: .01rem solid #c6c6c6;
            &:first-child{
                background-image: linear-gradient(rgb(76, 184, 196), rgb(60, 211, 173));
                color: #fff;
            }
        }
    }
    .directory-prefix{
        color: red;
    }
</style>
