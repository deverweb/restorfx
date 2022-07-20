<template>
  <div class="features">
    <div class="feature" >
      <svg class="feature-svg" width="12" height="48" viewBox="0 0 12 48" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M1 1L11 12.75V48" stroke="#FFC700" stroke-width="2" />
      </svg>
      <div class="feature-subtitle">{{ features.feauture_1.subtitle }}</div>
      <div class="feature-title">{{ features.feauture_1.title }}</div>
    </div>
    <div class="feature" >
      <svg class="feature-svg" width="12" height="48" viewBox="0 0 12 48" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M1 1L11 12.75V48" stroke="#FFC700" stroke-width="2" />
      </svg>
      <div class="feature-subtitle">{{ features.feauture_2.subtitle }}</div>
      <div class="feature-title">{{ features.feauture_2.title }}</div>
    </div>
    <div class="feature" >
      <svg class="feature-svg" width="12" height="48" viewBox="0 0 12 48" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M1 1L11 12.75V48" stroke="#FFC700" stroke-width="2" />
      </svg>
      <div class="feature-subtitle">{{ features.feauture_3.subtitle }}</div>
      <div class="feature-title">{{ features.feauture_3.title }}</div>
    </div>

  </div>
</template>

<script>
export default {
  props: ['features']
};
</script>

<style lang="sass" scoped>
.features
  display: flex
  // column-gap: 178px
  flex-direction: column
  align-items: flex-start
  gap: 47px
  max-width: 1043px
  width: 100%
  +rmin(1200)
    min-width: 600px
    flex-direction: row
    align-items: center
    justify-content: space-between
    gap: 0
.feature
  padding-left: 26px
  position: relative
  &-svg
    position: absolute
    left: -1px
    top: -5px
  &-title
    +ph
    font-size: 14px
    text-transform: uppercase
    color: white
    line-height: 18px
    letter-spacing: 1.4px
    +rmin(360)
      font-size: 16px
      line-height: 21px
  &-subtitle
    color: $gray
    font-size: 10px
    line-height: 12px
    margin-bottom: 4px
    letter-spacing: 0.9px
    +pb
    +rmin(360)
      font-size: 12px
      line-height: 15px

</style>