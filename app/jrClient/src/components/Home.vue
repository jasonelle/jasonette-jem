<template>
	<div class='home'>
    <div class='col-md-2'>
    </div>
    <div class='col-md-8'>
    <h2>Recent Jasonette Extensions</h2>
    <Spinner v-show="loading"></Spinner>
		<Item v-for="item in items" :item="item" v-show="!loading"></Item>
    </div>
    <div class='col-md-2'>
    </div>
	</div>
</template>
<script>
  import Item from './Item'
  import Spinner from './Spinner'

  export default {
    name: "list",
    components: {
      Item, Spinner
    },
    data () {
      return { items: [], loading: true }
    },
    created () {
      const self = this
      this.$http.get('https://jasonx.herokuapp.com/jrs.json').then((response) => {
        self.items = response.body
        this.loading = false
      }, (response) => { })
    }
  }
</script>
<style scoped lang="scss">
  .home{
    padding-top: 80px;
  }
  .home h1.logo{
    font-size: 100px;
    font-weight: bold;
    padding:0 20px;
  }
  h2{
    padding:20px;
    font-family: "HelveticaNeue-CondensedBold", "HelveticaNeueBoldCondensed", "HelveticaNeue-Bold-Condensed", "Helvetica Neue Bold Condensed", "HelveticaNeueBold", "HelveticaNeue-Bold", "Helvetica Neue Bold", "HelveticaNeue", "Helvetica Neue", 'TeXGyreHerosCnBold', "Helvetica", "Tahoma", "Geneva", "Arial Narrow", "Arial", sans-serif;
    font-weight: bold;
  }
  .home a{
    color: #202020 !important;
    font-size: 16px;
    padding: 10px 20px !important;
  }
  .home a h1{
    font-size: 20px !important;
    font-weight: bold;
    font-family: "HelveticaNeue-CondensedBold", "HelveticaNeueBoldCondensed", "HelveticaNeue-Bold-Condensed", "Helvetica Neue Bold Condensed", "HelveticaNeueBold", "HelveticaNeue-Bold", "Helvetica Neue Bold", "HelveticaNeue", "Helvetica Neue", 'TeXGyreHerosCnBold', "Helvetica", "Tahoma", "Geneva", "Arial Narrow", "Arial", sans-serif;
  }
</style>
