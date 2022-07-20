<template>
  <div class="car car__tesla">
    <div class="car-images">
      <img class="car-images-image car-images-image__full" src="@/assets/img/car_main/clear_car.png"  alt="Car"/>
      <img :class="'car-images-image car-image ' + service.dataName " :data-serviceImage="service.dataName" v-for="service, i in services" :key="i" :src="service.image" alt="Car" :style="`z-index:${service.zIndex}`">
    </div>
    <div class="car-services">
      <div :class="`service service__${service.dataName}`"   v-for="service,i in services" :key="i" :data-service="service.dataName" @click="hideServiceCarImage(service.dataName, $event)">
        <div class="service-item">
          <div class="service-item-icon">
           <svg width="64" height="64" viewBox="0 0 64 64" fill="none" xmlns="http://www.w3.org/2000/svg">
            <rect class="inner-box" x="32.5" y="13.7952" width="26.45" height="26.45" transform="rotate(45 32.5 13.7952)" stroke="#FFC700" stroke-width="1.15" stroke-dasharray="8.05 11.5"/>
            <rect class="inner-rect" opacity="0.36" x="32.5" y="21.9314" width="14.95" height="14.95" transform="rotate(45 32.5 21.9314)" fill="#FFC700"/>
            <rect :class="  {'active': service.isServiceHovering}" class="outer-box"   x="32.436" y="2" width="43.0428" height="43.0428" transform="rotate(45 32.436 2)" stroke="#FFC700" stroke-width="1.59418" stroke-dasharray="13.22 18.88"/>
            <rect :class=" {'active': service.isServiceHovering}" class="outer-rect"  x="32.436" y="23.4177" width="12.7534" height="12.7534" transform="rotate(45 32.436 23.4177)" fill="#FFC700"/>
          </svg>



          </div>
          <div class="service-item-text">
            <div class="service-item-wrapper">
              <div class="service-item-sub">{{service.subtitle}}</div>
              <div class="service-item-title">{{service.title}}</div>

            </div>
          </div>
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
        zIndex: 6,
        isShowing: true,
        
      },
      {
        title: 'DYNOFLEX',
        subtitle: 'Glass Protection',
        dataName: 'dynoflex',
        image: './assets/img/car_main/service_2_dynoflex.png',
        left: '348px',
        top: '-43px',
        zIndex: 6,
        isShowing: true,
        
      },
      {
        title: 'RESTOR FX',
        subtitle: 'Restoration',
        dataName: 'restorfx',
        image: './assets/img/car_main/service_3_restorfx.png',
        left: '595px',
        top: '210px',
        zIndex: 4,
        isShowing: true,
        
      },
      {
        title: 'PROTECTION',
        subtitle: 'Polyurethane Film',
        dataName: 'protection',
        image: './assets/img/car_main/service_4_protection.png',
        left: '80px',
        top: '68px',
        zIndex: 6,
        isShowing: true,
        
      },
      {
        title: 'DENT REPAIR',
        subtitle: 'Paintless',
        dataName: 'repair',
        image: './assets/img/car_main/service_5_repair.png',
        left: '323px',
        top: '296px',
        zIndex: 6,
        isShowing: true,
        
      },
    ]
  }),
 
  methods: {
    hideServiceCarImage: function(dataName, event) {
      let target = event.target.closest('.service')
      let car = target.closest('.car')
      let images = car.querySelector(`.car-images .${dataName}`)
      let item = this.services.find(arrItem => {
        return arrItem.dataName == target.dataset.service
      })
      if(item.isShowing) {
        gsap.to(images, {duration: 0.3, opacity: 0})
      } else {
        gsap.to(images, {duration: 0.3, opacity: 1})
      }
        item.isShowing = !item.isShowing

    }
  }
}
</script>

<style lang="sass">
img
  user-select: none
.service
  position: absolute
  z-index: 12
  
  &:hover
    .outer-box
      opacity: 1
    .outer-rect
      opacity: 1
    .inner-box
      stroke: #503F01
    .service-item
      &-text
        opacity: 1
  &__clearfx
    top: 36.8%
    left: -4.6%
  &__dynoflex
    left: 37.1%
    top: -6.6%
  &__restorfx
    left: 63.3%
    top: 32.2%
  &__protection
    
    left: 18%
    top: 8%
    +rmin(1200)
      left: 8.8%
      top: 10.5%
  &__repair
    top: 45.7%
    left: 34.6%
  &-item
    // position: absolute
    // z-index: 10
    height: 38px
    width: 38px
    border-radius: 50%
    padding: 0
    cursor: pointer
    display: flex
    align-items: center
    +rmin(600)
      width: 50px
      height: 50px

    +rmin(1200)
      width: auto
      height: 96px
    &-wrapper
      +rmin(1200)
        opacity: 1
        transition: opacity 0.2s ease-in-out
        display: flex
        align-items: flex-start
        flex-direction: column
        justify-content: center
    &-text
      display: none
      +rmin(1200)
        padding-left: 93px
        padding-right: 50px
        width: auto
        opacity: 0
        height: 100%
        border-radius: 49px
        overflow: hidden
        transition: opacity 0.2s ease-in-out
        background-color: rgba($black, 70%)
        display: flex
        align-items: center
        
    &-icon
      height: 38px
      background-color: rgba($black, 36%)
      border-radius: 50%
      position: absolute
      // left: 5px
      top: 50%
      padding: 3px
      transform: translateY(-50%)
      +rmin(600)
        height: 50px
        width: 50px
      +rmin(1200)
        height: 69px
        width: 69px
        left: 10px
        
      .outer-rect
        transition: opacity 0.3s ease-in-out
        opacity: 0
      .outer-box
        transition: opacity 0.3s ease-in-out
        stroke-dasharray: 21
        stroke-dashoffset: 9
        opacity: 0
      .inner-rect
      .inner-box
        stroke-dasharray: 13
        stroke-dashoffset: 6
      svg
        transition: all 0.3s ease-in-out
        width: 100%
        height: 100%
      rect
        transition: all 0.3s ease-in-out
    &-sub
      color: $gray
      +pd
      line-height: 8px
      font-size: 6px
      white-space: nowrap
      margin-bottom: 1px
      letter-spacing: 0.8px
      +rmin(1200)
        font-size: 10px
        line-height: 13px
        position: relative
        top: -1px
    &-title
      line-height: 10px
      font-size: 8px
      text-transform: uppercase
      color: white
      +ph
      letter-spacing: 1.1px
      white-space: nowrap
      +rmin(1200)
        font-size: 14px
        line-height: 18px

  img
    max-width: 100%
.car
  width: 100%
  height: auto
  z-index: 23
  position: relative
  left: 50%
  top: 37%
  transform: translateX(-50%)
  // +r(1660)
    // right: -5%
  +rmin(360)
    width: 100%
  +rmin(1200)
    // width: 50%
    position: absolute
    top: 37%
    right: -2.3%
    width: 49.3vw
    left: initial
    transform: none
    // bottom: 40px
  +rmin(1380)
    top: initial
    bottom: 0px
  +rmin(1660)
    bottom: -76px
    right: -7.3%

  &-services
    position: absolute
    top: 0
    left: 0
    right: 0
    bottom: 0
  &-images
    position: relative

    &-image
      position: absolute
      width: 100%
      left: 0
      top: 0
      &.restorfx
        left: 1.2px
      &__full
        position: relative
      &__service
</style>>