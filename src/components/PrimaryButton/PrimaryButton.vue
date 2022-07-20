<template>
  <button class="primary-button">
    <svg class="top-left" width="275" height="70" viewBox="0 0 275 70" fill="none" xmlns="http://www.w3.org/2000/svg">
      <rect x="1" y="1" width="273" height="68" rx="34" stroke="#FFC700" stroke-width="2"/>
    </svg>
    <svg class="bottom-right" width="275" height="70" viewBox="0 0 275 70" fill="none" xmlns="http://www.w3.org/2000/svg">
      <rect x="1" y="1" width="273" height="68" rx="34" stroke="#FFC700" stroke-width="2"/>
    </svg>

    <div class="primary-button-text"><slot /></div>
  </button>
</template>

<script>
export default {};
</script>

<style lang="sass" scoped>
.primary-button
  // font-size: 14px
  +ph
  color: white
  text-transform: uppercase
  padding: 25px 26px
  letter-spacing: 1.6px
  position: relative
  width: 275px
  max-width: 275px
  display: flex
  justify-content: center
  +rmin(1440)
    font-size: 16px
    padding: 25px 0px

  &:hover
    svg
      stroke-dasharray: 314 0
      stroke-dashoffset: -125
  .top-left
    transform: rotate(180deg)
    transform-origin: center
  svg
    position: absolute
    left: 0
    top: 0
    stroke-dasharray: 143 625
    stroke-dashoffset: -257
    transition: all 0.3s ease-out
  &-border
    z-index: -1
    position: absolute
    left: 50%
    top: 50%
    transform: translate(-50%, -50%)
</style>