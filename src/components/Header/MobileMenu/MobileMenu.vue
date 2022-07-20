<template>
  <div class="mmenu">
    <nav>
      <ul>
        <li><a href="#">ABOUT US</a></li>
        <li><a href="#">SERVICES</a></li>
        <li><a href="#">REVIEWS</a></li>
        <li><a href="#">MAP</a></li>
        <li><a href="#">CONTACTS</a></li>
      </ul>

    </nav>
    <MobileButton class="mmenu-btn">CALL ME BACK</MobileButton>
  </div>
</template>

<script>
import PrimaryButton from '../../PrimaryButton/PrimaryButton.vue';
import MobileButton from '../../MobileButton/MobileButton.vue';
export default {
    components: { PrimaryButton, MobileButton }
}
</script>

<style lang="sass" scoped>
.mmenu
  background-color: $black
  min-height: 100vh
  position: absolute
  top: 99px
  left: 0
  right: 0
  width: 100%
  z-index: -1
  padding: 47px 0px 0px
  display: flex
  flex-direction: column
  align-items: flex-start
  nav
    width: 100%
  ul
    display: flex
    flex-direction: column
  li
    padding: 7px 0px 14px 25px
    &:hover
      a
        background-position-x: -2px
        color: $black
        color: white
  a
    background-size: 128% 126%
    background-repeat: no-repeat
    background-image: url('/assets/img/menu/item_bg.png')
    background-position-x: -425px
    background-position-y: center
    font-size: 32px
    padding: 7px 42px 14px 25px
    text-transform: uppercase
    color: white
    +ph
    transition: all 0.3s  ease-in-out
  +rmin(1200)
    display: none !important
</style>

