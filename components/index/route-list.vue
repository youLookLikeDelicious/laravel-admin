<template>
  <div class="route-list">
    <table>
      <tr>
        <td v-for="(item, index) in title" :key="index">
          {{ item }}
        </td>
      </tr>
    </table>
    <div>
      <table>
        <tr v-for="(list, index) in resource.slice(1)" :key="index">
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
  div{
    overflow-y: auto;
  }
}
</style>
