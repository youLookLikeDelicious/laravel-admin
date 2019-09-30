<template>
  <div class="container">
    <div class="dash-bord">
      <ListBox v-for="(item, key) in resource.mvcList" :key="key" :resource="{'header': key, 'list': item}" />
      <RouteList :resource="resource.routeList" />
    </div>
  </div>
</template>

<script>
import ListBox from '@/components/index/list-box'
import RouteList from '@/components/index/route-list'
export default {
  name: 'Index',
  components: {
    ListBox,
    RouteList
  },
  data () {
    return {
      resource: {}
    }
  },
  mounted () {
    this.getResource()
  },
  methods: {
    getResource () {
      this.$axios({
        url: '/php-admin',
        method: 'get'
      }).then((response) => {
        this.resource = response.data
      }).catch((error) => {
        throw new Error(error)
      })
    }
  }
}
</script>

<style lang="scss">
.container{
  display: flex;
  height: 100%;
  overflow-x: auto;
  box-sizing: border-box;
}
.dash-bord{
  height: 100%;
  display: flex;
  justify-content: space-between;
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
  padding-left: 2.4rem;
  padding-right: 2.4rem;
  div{
    margin-right: 2.4rem;
  }
}
</style>
