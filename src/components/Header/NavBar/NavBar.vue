<template>
  <nav>
    <ul>
      <li :key="i" v-for="link, i in links">
        <a :class="{
          // 'active': (this.currentSlide == link.slide) || (this.currentSlide == link.anotherSlides)
          'active': link.slides.find(item => item == currentSlide)
        }" @click='animateSlideNav(link.slide, $event)' :href="link.route">{{link.label }}</a>
      </li>
     
    </ul>
  </nav>
</template>

<script>
export default {
  name: "NavBar",
  props: ['currentSlide'],
  watch: {
    currentSlide: function() {
      if(this.currentSlide == 2 || this.currentSlide == 3){
        this.links[0].active = 'active'
      }
    }
  },
  methods: {
    animateSlideNav: function(slide, event) {
      event.currentTarget.classList.add('active')
      this.$parent.animateSlideByClick(slide, event)
    }
  },
  data: () => ({
    links: [
      {
        route: '#about',
        label: 'About Us',
        slide: 2,
        slides: [2,3],
        // anotherSlides: 3
      },
      {
        route: '#services',
        label: 'Services',
        slide: 4,
        slides: [4,5,6,7,8],
      },
      {
        route: '#reviews',
        label: 'reviews',
        slide: 9,
        slides: [9],
      },
      {
        route: '#contacts',
        label: 'Contacts',
        slide: 11,
        slides: [11],
      },
    ]
  })
};
</script>

<style lang="sass" scoped>
.router-link-active
  color: $yellow
ul
  display: flex
  align-items: center
  column-gap: 84px
  text-transform: uppercase
  li
    &:hover
      a:not(.router-link-active)
        color: lighten($gray, 20%)
  a
    transition: color 0.2s ease-in-out
    color: $gray
    font-size: 12px
    +ph
    white-space: nowrap
    letter-spacing: 0.8px
    &.active
      transition-delay: 0.5s
      color: $yellow !important

      

</style>