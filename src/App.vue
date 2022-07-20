<template>
  <div class="app-container">
    <router-view class="page" />
  </div>
</template>

<style lang="sass">

#app
  font-family: Avenir, Helvetica, Arial, sans-serif
  -webkit-font-smoothing: antialiased
  -moz-osx-font-smoothing: grayscale
  position: relative
  height: auto
  // background-image: url('./assets/img/bglight.png')
  background-image: url('./assets/img/mobile_bg.png')
  background-position: right top
  background-size: contain
  background-repeat: no-repeat
  &.thanks
    background-size: cover
    +rmin(1199)
      background-size: contain
  +rmin(1199)
    height: 100%
    background-image: url('./assets/img/bglight.png')
    overflow: hidden
    padding: 56px 140px 70px 140px
  +r(1660)
    padding: 40px 70px 70px 70px
  +r(1199)
    padding: 0
  &.thanks
    .mobile-container
      overflow: hidden
.app-container
  display: flex
  flex-direction: column
  height: 100%
  position: relative
.page
  height: 100%

</style>

<script>
export default {
  name: 'Home',
  watch:{
    '$route' (to, from){
      if(to.name == 'Thanks'){
        document.querySelector('#app').classList.add('thanks')

      } else {
        document.querySelector('#app').classList.remove('thanks')
      }
        
    }
},
}
</script>
