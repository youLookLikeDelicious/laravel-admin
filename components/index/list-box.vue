<!--props数据结构
resource:
{
  header: '',
  list: []
}-->
<template>
  <div class="list-box">
    <p> {{ resource.header }} {{ itemNum }}</p>
    <ul>
      <li v-for="(item, index) in resource.list" :key="index" :style="{ textIndent: (( item.split('/').length || 1) - 1) * 2 + 'em' }" :class="{'directory-prefix': item.indexOf('.php') === -1}">
        {{ item.split('/').pop() }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'ListBox',
  props: {
    resource: {
      type: Object,
      default () {
        return {}
      }
    }
  },
  data () {
    return {
      itemNum: ' '
    }
  },
  mounted () {
    this.itemNum = this.resource.list.length - this.$el.querySelectorAll('li.directory-prefix').length
  }
}
</script>

<style lang="scss">
    .list-box{
        height: 97%;
        display: flex;
        flex-direction: column;
        list-style: none;
        background: #fff;
        border-top-left-radius: .3rem;
        border-top-right-radius: 1.5rem;
        overflow: hidden;
        p{
            flex: 0 1 2.5rem;
            line-height: 2.5rem;
            background-image: linear-gradient(rgb(76, 184, 196), rgb(60, 211, 173));
            color: #fff;
            padding-left: .4rem;
        }
        ul{
            overflow-x: hidden;
            overflow-y: scroll;
            list-style: none;
            flex: 1 1 auto;
            color: $list-font-color;
        }
        li{
            height: 2.1rem;
            padding: .5rem .5rem;
            -webkit-box-sizing: border-box;
            -moz-box-sizing: border-box;
            box-sizing: border-box;
            border-bottom: .01rem solid #c6c6c6;
        }
    }
    .directory-prefix{
        &:before{
            content: '▶';
            cursor: pointer;
        }
    }
</style>
