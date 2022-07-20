<template>
  <div class="container-wrapper">
    <div class="home-container">
      <header class="header">
        <div class="header-wrapper">
          <!-- <Logo @click="animateSlideByClick(1, $event)" class="header-logo"/> -->
          <Logo  class="header-logo"/>
          <!-- <div @click="animateSlideByClick(10, $event)"  class="header-map"> -->
          <div class="header-map">
              <div>
                <span class="header-map-icon">
                  <svg
                    width="13"
                    height="21"
                    viewBox="0 0 13 21"
                    fill="none"
                    xmlns="http://www.w3.org/2000/svg"
                  >
                    <path
                      d="M6.5 0C2.91005 0 0 2.91005 0 6.5C0 11.05 6.5 20.8 6.5 20.8C6.5 20.8 13 11.05 13 6.5C13 2.91005 10.0886 0 6.5 0ZM7.1045 11.6616C6.9056 11.6785 6.71125 11.7 6.5 11.7C6.28875 11.7 6.09375 11.6785 5.8955 11.6616C3.3085 11.362 1.3 9.1676 1.3 6.5C1.3 3.62765 3.62765 1.3 6.5 1.3C9.36975 1.3 11.7 3.62765 11.7 6.5C11.7 9.1676 9.6889 11.362 7.1045 11.6616Z"
                      fill="#FFC700"
                    />
                    <path
                      d="M6.50015 9.10001C7.93609 9.10001 9.10015 7.93595 9.10015 6.50001C9.10015 5.06407 7.93609 3.90001 6.50015 3.90001C5.06421 3.90001 3.90015 5.06407 3.90015 6.50001C3.90015 7.93595 5.06421 9.10001 6.50015 9.10001Z"
                      fill="#FFC700"
                    />
                  </svg>
                </span>
                <span class="header-map-text">735 N Edgewood Avenue<br>Unit F Wood Dale, IL, US 60191</span>
              </div>
          </div>
          <!-- <NavBar :currentSlide="currentSlide" class="header-navbar"></NavBar> -->
          

        

        </div>
      </header>
      <!-- <Tesla class="offer-car" /> -->
      <div class="car car__tesla">
        <div class="car-images">
          <img class="car-images-image car-images-image__full" src="@/assets/img/car_main/clear_car.png"  alt="Car"/>
          <img :class="'car-images-image car-image ' + service.dataName " :data-serviceImage="service.dataName" v-for="service, i in services" :key="i" :src="service.image" alt="Car" :style="`z-index:${service.zIndex}`">
        </div>
        <div class="car-services">
          <div :class="`service service__${service.dataName}`"   v-for="service,i in services" :key="i" :data-service="service.dataName" @click="hideServiceCarImage(service.dataName, $event, services)">
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
      <Features class="offer-features" :features="offerFeatures"></Features>
      <section class="offer slide slide__1">
        <div ref="wrapper" class="offer-wrapper " data-slide="1">
          <!-- <div class="animated"> -->
            <div class="offer-sub">THANK YOU!</div>
            <div class="offer-title">WAIT FOR<br>THE CALL</div>
            <p class="offer-text">
              Thanks for the application! The manager has already received your request and will contact you soon!
            </p>
            <PrimaryButton @click="$router.push({name: 'Home'})" class="offer-btn">BACK TO SITE</PrimaryButton>
          <!-- </div> -->
        </div>
        
       
        
      </section>
    </div>
    <div class="mobile-container">
    
      <header class="header">
          <div class="header-wrapper">
            <Logo class="header-logo"/>
            <!-- <Map data-slideto="map" @click.prevent="scrollToSection" class="header-map"/> -->
            <div data-slideTo="map" @click.prevent.stop="scrollToSection"  class="header-map">
                <div>
                  <span class="header-map-icon">
                    <svg
                      width="13"
                      height="21"
                      viewBox="0 0 13 21"
                      fill="none"
                      xmlns="http://www.w3.org/2000/svg"
                    >
                      <path
                        d="M6.5 0C2.91005 0 0 2.91005 0 6.5C0 11.05 6.5 20.8 6.5 20.8C6.5 20.8 13 11.05 13 6.5C13 2.91005 10.0886 0 6.5 0ZM7.1045 11.6616C6.9056 11.6785 6.71125 11.7 6.5 11.7C6.28875 11.7 6.09375 11.6785 5.8955 11.6616C3.3085 11.362 1.3 9.1676 1.3 6.5C1.3 3.62765 3.62765 1.3 6.5 1.3C9.36975 1.3 11.7 3.62765 11.7 6.5C11.7 9.1676 9.6889 11.362 7.1045 11.6616Z"
                        fill="#FFC700"
                      />
                      <path
                        d="M6.50015 9.10001C7.93609 9.10001 9.10015 7.93595 9.10015 6.50001C9.10015 5.06407 7.93609 3.90001 6.50015 3.90001C5.06421 3.90001 3.90015 5.06407 3.90015 6.50001C3.90015 7.93595 5.06421 9.10001 6.50015 9.10001Z"
                        fill="#FFC700"
                      />
                    </svg>
                  </span>
                  <span class="header-map-text">735 N Edgewood Avenue<br>Unit F Wood Dale, IL, US 60191</span>
                </div>
              </div>
            <Phone class="header-phone" :tel="tel"></Phone>
            <!-- <Gamb class="header-gamb" @click="showMenu = true" :class="{active: showMenu}"></Gamb> -->
            <!-- <button class="header-menu" @click="showMenu = true">
              <svg width="22" height="11" viewBox="0 0 22 11" fill="none" xmlns="http://www.w3.org/2000/svg">
                <rect x="0.211914" width="21" height="2" fill="#050502"/>
                <rect x="0.211914" y="9" width="21" height="2" fill="#050502"/>
              </svg>

            </button> -->

          

          </div>
        </header>
      
      <section class="offer">
        <div class="offer-subtitle subtitle">THANK YOU</div>
        <h1 class="offer-title title">WAIT FOR<br>THE CALL</h1>
        <p class="offer-text text">Thanks for the application! The manager has already received your request and will contact you soon!.</p>
        <MobileButton @click="$router.push({name: 'Home'})"   class="offer-btn offer-btn__mobile">BACK TO SITE</MobileButton>
        <PrimaryButton @click="$router.push({name: 'Home'})" class="offer-btn offer-btn__desktop">BACK TO SITE</PrimaryButton>
        <Tesla class="offer-car"></Tesla>
        <Features class="offer-features" :features="offerFeatures"></Features>
      </section>
        
    
    </div>
    <transition name="slideout">
      <div class="mmenu" v-show="showMenu" >
        <div class="mmenu-wrapper">
          <div class="mmenu-top">
            <Logo class="header-logo"/>
            <Map class="header-map"/>
            <NavBar class="header-navbar"></NavBar>
            <Phone class="header-phone" :tel="tel"></Phone>
            <!-- <Gamb class="header-gamb" @click="showMenu = true" :class="{active: showMenu}"></Gamb> -->
            <button class="mmenu-close" @click="showMenu = false">
              <svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M1 1L10 10M19 19L10 10M10 10L19 1L1 19" stroke="#0B0B0B" stroke-width="2"/>
              </svg>
            </button>

          </div>
          <nav>
            <ul>
              <li><a data-slideTo="about" href="#about" @click.prevent="scrollToSection" >ABOUT US</a></li>
              <li><a data-slideTo="services" href="#services" @click.prevent="scrollToSection">SERVICES</a></li>
              <li><a data-slideTo="reviews" href="#reviews" @click.prevent="scrollToSection">REVIEWS</a></li>
              <li><a data-slideTo="map" href="#map" @click.prevent="scrollToSection">MAP</a></li>
              <li><a data-slideTo="contact" href="#contact" @click.prevent="scrollToSection">CONTACTS</a></li>
            </ul>

          </nav>
          <MobileButton @click="showPopup = true"  class="mmenu-btn">Get in touch</MobileButton>

        </div>
      </div>
    </transition>
    <transition name="slideout">
      <div class="popup" v-show="showPopup">
        <div class="popup-mobile">
          <div class="popup-wrapper">
            <div class="popup-top">
              <Logo class="header-logo"/>
              <Map class="header-map"/>
              <NavBar class="header-navbar"></NavBar>
              <Phone class="header-phone" :tel="tel"></Phone>
              <!-- <Gamb class="header-gamb" @click="showMenu = true" :class="{active: showMenu}"></Gamb> -->
              <button class="popup-close" @click="showPopup = false">
                <svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
                  <path d="M1 1L10 10M19 19L10 10M10 10L19 1L1 19" stroke="#0B0B0B" stroke-width="2"/>
                </svg>
              </button>
    
            </div>
            <div class="popup-subtitle subtitle">GET IT TOUCH</div>
            <p class="popup-text text">Please leave your phone number in the form below and our manager will contact you soon!</p>
            <RestorForm class="popup-form"></RestorForm>
  
          </div>
        </div>
        <div class="popup-desktop">
          
          <div class="header">
            <div class="header-wrapper">
              <!-- <Logo @click="animateSlideByClick(1, $event)" class="header-logo"/> -->
              <Logo  class="header-logo"/>
              <!-- <div @click="animateSlideByClick(10, $event)"  class="header-map"> -->
              <div class="header-map">
                  <div>
                    <span class="header-map-icon">
                      <svg
                        width="13"
                        height="21"
                        viewBox="0 0 13 21"
                        fill="none"
                        xmlns="http://www.w3.org/2000/svg"
                      >
                        <path
                          d="M6.5 0C2.91005 0 0 2.91005 0 6.5C0 11.05 6.5 20.8 6.5 20.8C6.5 20.8 13 11.05 13 6.5C13 2.91005 10.0886 0 6.5 0ZM7.1045 11.6616C6.9056 11.6785 6.71125 11.7 6.5 11.7C6.28875 11.7 6.09375 11.6785 5.8955 11.6616C3.3085 11.362 1.3 9.1676 1.3 6.5C1.3 3.62765 3.62765 1.3 6.5 1.3C9.36975 1.3 11.7 3.62765 11.7 6.5C11.7 9.1676 9.6889 11.362 7.1045 11.6616Z"
                          fill="#FFC700"
                        />
                        <path
                          d="M6.50015 9.10001C7.93609 9.10001 9.10015 7.93595 9.10015 6.50001C9.10015 5.06407 7.93609 3.90001 6.50015 3.90001C5.06421 3.90001 3.90015 5.06407 3.90015 6.50001C3.90015 7.93595 5.06421 9.10001 6.50015 9.10001Z"
                          fill="#FFC700"
                        />
                      </svg>
                    </span>
                    <span class="header-map-text">735 N Edgewood Avenue<br>Unit F Wood Dale, IL, US 60191</span>
                  </div>
              </div>
                
              <button class="popup-close" @click="showPopup = false">
                <svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
                  <path d="M1 1L10 10M19 19L10 10M10 10L19 1L1 19" stroke="#0B0B0B" stroke-width="2"/>
                </svg>
              </button>
              

            

            </div>
          </div>
          <div class="popup-contacts">
            <div class="contacts-left">
            
              <div class="contacts-subtitle subtitle">Get in touch<br>with us</div>
              <p class="contacts-text text">Please leave your phone number in the form below and our manager will contacts you soon!</p>
              <RestorForm class="contacts-form"></RestorForm>
            </div>
  
            <div class="contacts-right">
              <div class="contacts-wrapper">
                <div class="contacts-col contacts-phones">
                  <div class="contacts-item-title">
                    CALL CENTRE
                  </div>
                  <div class="contacts-item-items">
                    <a href="tel:(708) 887 99 88">
                      <img :src="'./assets/img/contacts/bg.png'">
                      (708) 887 99 88</a>
                    <a href="tel:(224) 900 00 15">
                      <img :src="'./assets/img/contacts/bg.png'">
                      (224) 900 00 15</a>
                    <a href="tel:(224) 830 11 45">
                      <img :src="'./assets/img/contacts/bg.png'">
                      (224) 830 11 45</a>
                  </div>
                </div>
                <div class="contacts-col contacts-social">
                  <div class="contacts-item">
                    <div class="contacts-item-title">SOCIAL NETWORKS</div>
                    <div class="contacts-item-items">
                      <a href="#">
                        <img :src="'./assets/img/contacts/soc-bg.png'">
                        INSTAGRAM</a>
                      <a href="#">
                        <img :src="'./assets/img/contacts/soc-bg.png'">
                        FACEBOOK</a>
                    </div>
                  </div>
                  <div class="contacts-item">
                    <div class="contacts-item-title">Messenger</div>
                    <div class="contacts-item-items">
                      <a href="#">
                        <img :src="'./assets/img/contacts/soc-bg.png'">
                        WHATSAPP</a>
                    </div>
                  </div>
                </div>
              </div>
              <div class="contacts-email">
                <div class="contacts-item">
                  <div class="contacts-item-title">E-MAIL</div>
                  <div class="contacts-item-items">
                    <a href="#">info@restorfxwooddale.com</a>
                  </div>
                </div>
              </div>
            </div>

          </div>
        </div>
      </div>
    </transition>

  </div>
</template>

<script>
import gsap from "gsap";

import {Form, Field, ErrorMessage} from 'vee-validate'
import 'swiper/swiper-bundle.min.css'
// import 'swiper/css/navigation'
import NavBar from '@/components/Header/NavBar/NavBar.vue'
import Logo from '@/components/Header/Logo/Logo.vue'
import Map from '@/components/Header/Map/Map.vue'
import Gamb from '@/components/Header/Gamb/Gamb.vue'
import Phone from '@/components/Header/Phone/Phone.vue'
import PrimaryButton from "@/components/PrimaryButton/PrimaryButton.vue";
import Features from "@/components/Features/Features.vue";
import Car from "@/components/Car/Car.vue";
import Tesla from "@/components/Tesla/Tesla.vue";
import MobileMenu from '@/components/Header/MobileMenu/MobileMenu.vue'
import MobileButton from "../components/MobileButton/MobileButton.vue";
import RestorForm from '@/components/RestorForm/RestorForm.vue'
// import 
// import Header from "../components/Header/Header.vue";

export default {
  name: "Thanks",
  
  components: {
    PrimaryButton,
    Features,
    Car,
    Tesla,
    MobileButton,
    MobileMenu,
    NavBar,
    Logo,
    Map,
    Phone,
    Gamb,
    Form,
    Field,
    ErrorMessage,
    RestorForm,
  },
  data: () => ({
    tel: '(708) 887 99 88',
    
   
    services: [
      {
        title: 'Clear FX',
        subtitle: 'Ceramic Coat',
        dataName: 'clearfx',
        image: './assets/img/car_main/service_1_clearfx.png',
        zIndex: 6,
        isShowing: true,
        
      },
      {
        title: 'DYNOFLEX',
        subtitle: 'Glass Protection',
        dataName: 'dynoflex',
        image: './assets/img/car_main/service_2_dynoflex.png',
        zIndex: 6,
        isShowing: true,
        
      },
      {
        title: 'RESTOR FX',
        subtitle: 'Restoration',
        dataName: 'restorfx',
        image: './assets/img/car_main/service_3_restorfx.png',
        zIndex: 4,
        isShowing: true,
        
      },
      {
        title: 'PROTECTION',
        subtitle: 'Polyurethane Film',
        dataName: 'protection',
        image: './assets/img/car_main/service_4_protection.png',
        zIndex: 6,
        isShowing: true,
        
      },
      {
        title: 'DENT REPAIR',
        subtitle: 'Paintless',
        dataName: 'repair',
        image: './assets/img/car_main/service_5_repair.png',
        zIndex: 6,
        isShowing: true,
        
      },
    ],
    contactForm: {
      isRequired: true,
      name: '',
      phone: ''
    },
    
    showMenu: false,
    showPopup: false,
    showVideo: false,
    
    servicesSlider: [
      {
        title: 'RESTOR FX',
        text: 'RestorFX is a professional restoration system that permanently brings the surface of a vehicle back to the durability and luster of its original paint finish.',
        component: 'Tesla',
        items: [
          {
            subtitle: 'The Cover Will Shine',
            title: 'Restores Paint'
          },
          
          {
            subtitle: 'Doesn’t Wash Off',
            title: 'ETERNAL COVERAGE'
          },
          
          {
            subtitle: 'Additional UV Protection',
            title: '100% PROTECTION'
          }
          
        ]
      },
      {
        title: 'RESTOR FX',
        text: 'RestorFX is a professional restoration system that permanently brings the surface of a vehicle back to the durability and luster of its original paint finish.',
        component: 'Tesla',
        items: [
          {
            subtitle: 'The Cover Will Shine',
            title: 'Restores Paint'
          },
          
          {
            subtitle: 'Doesn’t Wash Off',
            title: 'ETERNAL COVERAGE'
          },
          
          {
            subtitle: 'Additional UV Protection',
            title: '100% PROTECTION'
          }
          
        ]
      },
      {
        title: 'RESTOR FX',
        text: 'RestorFX is a professional restoration system that permanently brings the surface of a vehicle back to the durability and luster of its original paint finish.',
        component: 'Tesla',
        items: [
          {
            subtitle: 'The Cover Will Shine',
            title: 'Restores Paint'
          },
          
          {
            subtitle: 'Doesn’t Wash Off',
            title: 'ETERNAL COVERAGE'
          },
          
          {
            subtitle: 'Additional UV Protection',
            title: '100% PROTECTION'
          }
          
        ]
      },
      {
        title: 'RESTOR FX',
        text: 'RestorFX is a professional restoration system that permanently brings the surface of a vehicle back to the durability and luster of its original paint finish.',
        component: 'Tesla',
        items: [
          {
            subtitle: 'The Cover Will Shine',
            title: 'Restores Paint'
          },
          
          {
            subtitle: 'Doesn’t Wash Off',
            title: 'ETERNAL COVERAGE'
          },
          
          {
            subtitle: 'Additional UV Protection',
            title: '100% PROTECTION'
          }
          
        ]
      },
    ],
    offerFeatures: [
      {
        title: "RESTOR FX",
        subtitle: "Restoration",
      },
      {
        title: "DENT REPAIR",
        subtitle: "Paintless",
      },
      {
        title: "CLEAR FX",
        subtitle: "Creamic Coat",
      },
    ],
  }),
  mounted() {
    document.body.style.overflow = 'auto'
    document.body.style.paddingRight = 0

  },
  created(){
    window.addEventListener('scroll', this.setHeaderFixed);
  },
  methods: {
    hideServiceCarImage: function(dataName, event, arr) {
      let target = event.target.closest('.service')
      let car = target.closest('.car')
      let images = car.querySelector(`.car-images .${dataName}`)
      let item = arr.find(arrItem => {
        return arrItem.dataName == target.dataset.service
      })
      if(item.isShowing) {
        gsap.to(images, {duration: 0.3, opacity: 0})
      } else {
        gsap.to(images, {duration: 0.3, opacity: 1})
      }
        item.isShowing = !item.isShowing

    },
    
    
    contactFormSubmit(values, actions) {
      actions.resetForm();
    },
    validateRequired(value) {
      if(!value) return 'This field is required'
      return true;
    },
    
    bodyPopupStyles(someVar) {
      this.scrollWidth = window.innerWidth - document.body.offsetWidth
      document.body.style.overflow = someVar ? 'hidden' : 'auto'
      document.body.style.paddingRight = someVar ? this.scrollWidth + 'px' : '0px'
    }
  },
  watch: {
  
    showMenu: function(){
      this.bodyPopupStyles(this.showMenu)
      if(this.showMenu) {
        // document.querySelector('.mmenu').style.paddingRight = this.scrollWidth + 'px'
        document.body.classList.add('body-popup')
        
      } else {
        // document.querySelector('.mmenu').style.paddingRight = '0px'
        document.body.classList.remove('body-popup')

      }
    },
    showPopup() {
      this.bodyPopupStyles(this.showPopup)
    },
    showVideo() {
      this.bodyPopupStyles(this.showVideo)
     
    }
  },
  
  created() {
    document.title = "Restor FX";
  },
};
</script>

<style>

</style>