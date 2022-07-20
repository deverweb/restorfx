<template>
  <div class="car">
    <div class="car-images">
      <img class="car-images-image car-images-image__full" src="@/assets/img/car_main/clear_car.png"  alt="Car"/>
      <img :class="'car-images-image car-image ' + service.dataName " :data-serviceImage="service.dataName" v-for="service, i in services" :key="i" :src="service.image" alt="Car" :style="`z-index:${service.zIndex}`">
    </div>
    <div class="car-services">
      <div class="service"  :style="'left:'+service.left+'; top:'+service.top" v-for="service,i in services" :key="i" :data-service="service.dataName" @click="hideServiceCarImage(service.dataName)">
        <div class="service-item">
          <div class="service-item-icon">
           <svg width="64" height="64" viewBox="0 0 64 64" fill="none" xmlns="http://www.w3.org/2000/svg">
            <rect class="inner-box" x="32.5" y="13.7952" width="26.45" height="26.45" transform="rotate(45 32.5 13.7952)" stroke="#FFC700" stroke-width="1.15" stroke-dasharray="8.05 11.5"/>
            <rect opacity="0.36" x="32.5" y="21.9314" width="14.95" height="14.95" transform="rotate(45 32.5 21.9314)" fill="#FFC700"/>
            <rect class="outer-box" x="32.436" y="2" width="43.0428" height="43.0428" transform="rotate(45 32.436 2)" stroke="#FFC700" stroke-width="1.59418" stroke-dasharray="13.22 18.88"/>
            <rect x="32.436" y="23.4177" width="12.7534" height="12.7534" transform="rotate(45 32.436 23.4177)" fill="#FFC700"/>
          </svg>



          </div>
          <div class="service-item-sub">{{service.subtitle}}</div>
          <div class="service-item-title">{{service.title}}</div>
        </div>
      </div>
    </div>
    
  </div>
</template>

<script>
import gsap from 'gsap'

export default {
  data: () => ({
    services: [
      {
        title: 'Clear FX',
        subtitle: 'Ceramic Coat',
        dataName: 'clearfx',
        image: './assets/img/car_main/service_1_clearfx.png',
        left: '-46px',
        top: '238px',
        zIndex: 6
      },
      {
        title: 'DYNOFLEX',
        subtitle: 'Glass Protection',
        dataName: 'dynoflex',
        image: './assets/img/car_main/service_2_dynoflex.png',
        left: '348px',
        top: '-43px',
        zIndex: 6
      },
      {
        title: 'RESTOR FX',
        subtitle: 'Restoration',
        dataName: 'restorfx',
        image: './assets/img/car_main/service_3_restorfx.png',
        left: '595px',
        top: '210px',
        zIndex: 4
      },
      {
        title: 'PROTECTION',
        subtitle: 'Polyurethane Film',
        dataName: 'protection',
        image: './assets/img/car_main/service_4_protection.png',
        left: '80px',
        top: '68px',
        zIndex: 6
      },
      {
        title: 'DENT REPAIR',
        subtitle: 'Paintless',
        dataName: 'repair',
        image: './assets/img/car_main/service_5_repair.png',
        left: '323px',
        top: '296px',
        zIndex: 6
      },
    ]
  }),
  methods: {
    hideServiceCarImage: function(dataName) {
      gsap.to(`.car-images .${dataName}`, {duration: 0.3, opacity: 0})
    }
  }
}
</script>

<style lang="sass" scoped>
img
  user-select: none
  // .service-image
    // position: relative
    // left: 2px
.service
  position: absolute
  z-index: 12
  &-item
    // position: absolute
    // z-index: 10
    height: 38px
    background-color: rgba($black, 70%)
    border-radius: 48px
    padding: 30px 51px 33px
    padding-left: 94px
    cursor: pointer
    &-icon
      background-color: rgba($black, 36%)
      border-radius: 50%
      position: absolute
      left: 11px
      top: 50%
      padding: 3px
      transform: translateY(-50%)
      .inner-box
        stroke-dasharray: 13
        stroke-dashoffset: 6
      .outer-box
        stroke-dasharray: 21
        stroke-dashoffset: 9
      svg
        width: 100%
        height: 100%
    &-sub
      color: $gray
      +pd
      line-height: 13px
      font-size: 10px
      white-space: nowrap
      margin-bottom: 1px
      letter-spacing: 0.8px
    &-title
      line-height: 18px
      font-size: 14px
      text-transform: uppercase
      color: white
      +ph
      letter-spacing: 1.1px
      white-space: nowrap
  img
    max-width: 100%
.car
  width: 942px
  height: 440px
  z-index: 23
  &-services
    position: relative
  &-image
    &.restorfx
      left: 1px
  &-images
    position: relative
    &-image
      position: absolute
      width: 100%
      &__full
        // width: 943px
      &__service
</style>>

