<template>
  <header class="header">
    <div class="header-wrapper">
      <Logo class="header-logo"/>
      <Map class="header-map"/>
      <NavBar class="header-navbar"></NavBar>
      <Phone class="header-phone" :tel="tel"></Phone>
      <Gamb class="header-gamb" @click="showMenu = !showMenu" :class="{active: showMenu}"></Gamb>
     

    </div>
  </header>
</template>

<script>
import gsap from 'gsap'


import NavBar from './NavBar/NavBar.vue'
import Logo from './Logo/Logo.vue'
import Map from './Map/Map.vue'
import MobileMenu from './MobileMenu/MobileMenu.vue'
import Gamb from './Gamb/Gamb.vue'
import Phone from './Phone/Phone.vue'
export default {
  data: () => ({
    tel: '(708) 887 99 88',
    showMenu: false
  }),
  methods: {
    
  },
  name: 'Header',
  components: {
    Logo,
    Map,
    NavBar,
    MobileMenu,
    Gamb,
    Phone,
}
}
</script>

<style lang="sass">

.header
  z-index: 50
  top: 0px
  width: 100%
  position: relative
  position: fixed
  padding: 20px 25px
  background-color: black
  right: 0
  left: 0
  +rmin(1440)
    padding: 0
    background-color: transparent
    border: none
  &-wrapper
    align-items: center
    display: flex
  &-logo
    svg
      width: 160px
  &-phone
    margin-left: auto
    margin-right: 20px
  &-navbar
    display: none
    +rmin(1439)
      display: flex
  &-map
    margin-left: auto
    flex-basis: 400px
    display: none
    +rmin(1439)
      display: flex
  &-phone
    +rmin(1440)
      display: none !important
  &-gamb
    +rmin(1440)
      display: none !important
  

</style>