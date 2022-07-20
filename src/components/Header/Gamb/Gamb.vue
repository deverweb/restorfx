<template>
  <!-- <button @click="e => e.target.classList.toggle('active')" class="gamb"> -->
  <button class="gamb">
    <span></span>
    <span></span>
  </button>
</template>

<script>
export default {
  data: () => ({
    isActive: false
  }),
}
</script>

<style lang="sass" scoped>
.gamb
  width: 58px
  height: 58px
  border-radius: 50%
  display: flex
  background-color: $yellow
  flex-shrink: 0
  gap: 6px
  position: relative
  span
    position: absolute
    width: 21px
    height: 2px
    background-color: black
    transform: translate(-50%, -50%)
    transition: all 0.2s ease-in-out
    left: 50%
    transform-origin: center
    &:first-child
      top: calc(50% - 4px)
    &:last-child
      top: calc(50% + 5px)
  &.active
    span
      top: 50%
      &:first-child
        transform: translate(-50%, -50%) rotate(45deg)
        
      &:last-child
        transform: translate(-50%, -50%) rotate(-45deg)
</style>>
