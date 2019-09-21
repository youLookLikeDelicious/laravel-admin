<template>
  <div class="container">
    <div class="dash-bord">
      <ul>
        <listBox :resource="controllerList" />
      </ul>
      <ul>
        <li>Model</li>
      </ul>
      <ul>
        <li>View</li>
        <li>1</li>
      </ul>
    </div>
  </div>
</template>

<script>
import listBox from '@/components/index/list-box'
export default {
  name: 'index',
  data () {
    return {
      controllerList: []
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
        this.controllerList = response.data
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
  .dash-bord{
    display: grid;
    grid-template-columns: auto auto auto;
    justify-items: center;
  }
</style>
