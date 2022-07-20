<template>
   <button class="primary-button">
    <svg class="top-left" width="340" height="71" viewBox="0 0 340 71" fill="none" xmlns="http://www.w3.org/2000/svg">
  <rect x="1" y="1.05615" width="338" height="68" rx="34" stroke="#FFC700" stroke-width="2"/>
  </svg>

    <svg class="bottom-right" width="340" height="71" viewBox="0 0 340 71" fill="none" xmlns="http://www.w3.org/2000/svg">
<rect x="1" y="1.05615" width="338" height="68" rx="34" stroke="#FFC700" stroke-width="2"/>
</svg>


    <div class="primary-button-text"><slot /></div>
  </button>
</template>

<script>
export default {

}
</script>

<style lang="sass" scoped>
.primary-button
  // font-size: 14px
  +ph
  color: white
  text-transform: uppercase
  padding: 25px 6px
  letter-spacing: 1.6px
  position: relative
  width: 100%
  justify-content: center
  align-items: center
  display: flex
  max-width: 340px
  &:hover
    svg
      stroke-dasharray: 160% 202%
      stroke-dashoffset: 308%
  .top-left
    top: -1px
    
  svg
    position: absolute
    width: 100%
    left: 0
    top: 0
    // left: 50%
    // top: 50%
    // transform: translate(-50%, -50%)
    stroke-dasharray: 80% 172%
    stroke-dashoffset: 120%
    transition: all 0.3s ease-out
    &.top-left
      transform: rotate(180deg)
  &-border
    z-index: -1
    position: absolute
    left: 50%
    top: 50%
    transform: translate(-50%, -50%)
</style>