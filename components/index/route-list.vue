<template>
  <div class="route-list">
    <!--<table>-->
      <!--<tr>-->
        <!--<td v-for="(item, index) in title" :key="index">-->
          <!--{{ item }}-->
        <!--</td>-->
      <!--</tr>-->
    <!--</table>-->
    <div>
      <table>
        <tr v-for="(list, index) in resource" :key="index">
          <td v-for="(item, ind) in list" :key="ind">
            {{ item }}
          </td>
        </tr>
      </table>
    </div>
  </div>
</template>

<script>
export default {
  name: 'RouteList',
  props: {
    resource: {
      type: Array,
      default () {
        return []
      }
    }
  },
  computed: {
    title () {
      return this.resource[0]
    }
  }
}
</script>

<style lang="scss">
.route-list{
  display: flex;
  background-color: #fff;
  flex-direction: column;
  color: $list-font-color;
  height: 97%;
  div{
    overflow-y: auto;
  }
  table, table tr, talbe td{
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    box-sizing: border-box;
  }
  table{
    $tr-height: 3.5rem;
    tr{
      &:first-child{
        position: absolute;
        height: $tr-height;
        top: 0;
        td{
          height: $tr-height;
        }
      }
      &:nth-child(2){
        margin-top: $tr-height;
      }
    }
    td{
      padding: .2rem .3rem;
      border: 1px solid red;
    }
  }
}
</style>
