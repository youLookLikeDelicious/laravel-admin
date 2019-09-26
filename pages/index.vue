<template>
  <div class="container">
    <div class="dash-bord">
      <listBox v-for="(item, key) in resourceList" :resource="{'header': key, 'list': item}" :key="key" />
    </div>
  </div>
</template>

<script>
import listBox from '@/components/index/list-box'
export default {
  name: 'index',
  data () {
    return {
      resourceList: []
    }
  },
  components: {
    listBox
  },
  methods: {
    getList () {
      this.$axios({
        url: '/php-admin',
        method: 'get'
      }).then((response) => {
        this.resourceList = response.data
      }).catch((error) => {
        console.log(error)
      })
    }
  },
  mounted () {
    this.getList()
  }
}
</script>

<style lang="scss">
  .container{
    height: 100%;
  }
  .dash-bord{
    height: 100%;
    display: flex;
    justify-content: space-evenly;
  }
</style>
