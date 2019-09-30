<template>
  <div class="route-list">
    <table>
      <tr>
        <td v-for="(item, index) in title" :key="index" :style="{width: `${tdWidthList[index]}px}`}">
          {{ item }}
        </td>
      </tr>
    </table>
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
    },
    tdWidthList () {
      if (!this.$el && !this.resource.length) {
        return []
      }

      const trs = this.$el.querySelectorAll('table')[1]
      const tds = trs.querySelectorAll('td')
      const widthList = []

      for (let i = 0, len = tds.length; i < len; i++) {
        widthList.push(tds[i].getComputedStyle('width'))
      }

      return widthList
    }
  },
  mounted () {
    const table = this.$el.querySelectorAll('table')[1]
    console.log(table.rows[0])
  }
}
</script>

<style lang="scss">
.route-list{
  display: flex;
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
    border-radius: .3rem;
    background-color: #fff;
    tr{

    }
    td{
      padding: .2rem .7rem;
      border-left: .1rem solid #c6c6c6;
      border-bottom: .1rem solid #c6c6c6;
    }
  }
}
</style>
