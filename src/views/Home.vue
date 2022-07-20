<template>
  <div class="container-wrapper ">
    <div class="home-container" @wheel='animateSlide' >
      <header class="header">
        <div class="header-wrapper">
          <Logo @click="animateSlideByClick(1, $event)" class="header-logo"/>
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
          <NavBar :currentSlide="currentSlide" class="header-navbar"></NavBar>




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
      <Features class="offer-features" :features="wpData.offer_features"></Features>
      <section class="offer slide slide__1">
        <div ref="wrapper" class="offer-wrapper " data-slide="1">
          <!-- <div class="animated"> -->
            <div class="offer-sub" v-html="wpData.offer_subtitle"></div>
            <!-- <div class="offer-title">CARE FOR<br />YOUR CAR</div> -->
            <div class="offer-title" v-html="wpData.offer_title"></div>
            <p class="offer-text" v-html="wpData.offer_text">

            </p>

            <PrimaryButton @click="showPopup = true" class="offer-btn">GET IN TOUCH</PrimaryButton>
          <!-- </div> -->
        </div>



      </section>
      <section class="about slide slide__2" data-slide='2'>
        <button class="about-return notshow" @click="animateSlideByClick(1, $event)">
          <svg
            width="10"
            height="16"
            viewBox="0 0 10 16"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              d="M9 1L1.92893 8.07107L8.81515 14.9573"
              stroke="white"
              stroke-width="2"
            />
          </svg>
          <div class="about-return-text">
            back
          </div>
        </button>
        <!-- <div class="about-wrapper about-wrapper__1" > -->
          <div class="animated animated__about-subtitle">
            <div class="about-subtitle" v-html="wpData.about_subtitle"></div>
          </div>
          <div class="animated animated__about-title">

            <div class="about-title " v-html="wpData.about_title"></div>
          </div>
          <!-- <div class="animated"> -->
            <div class="about-text">
              <div class="animated animated__about-text-1">
                <p class="text-1" v-html="wpData.about_text_1">

                </p>

              </div>
              <div class="animated animated__about-text-2" >
              <p class="text-2" v-html="wpData.about_text_2">

              </p>
              </div>

            </div>

          <!-- </div> -->
          <div class="about-video notshow" @click="showVideo = true">
            <div class="about-video-icon">
              <svg width="74" height="74" viewBox="0 0 74 74" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M32 28L47 37L32 46V28Z" fill="white"/>
                <circle cx="37" cy="37" r="36" stroke="#FFC700" stroke-width="2"/>
              </svg>
            </div>
            <div class="about-video-text">WATCH VIDEO PRESENTATION</div>
          </div>
        <!-- </div> -->


      </section>
      <PrimaryButton @click="showPopup =true" class="choose-btn notshow">Get in touch</PrimaryButton>
      <img :src="'./assets/img/about/about-bg.png'" class="about-bg notshow" >
      <img :src="'./assets/img/choose/choose-car.png'" class="choose-car notshow" >
      <section class="choose slide slide__3">
        <div class="choose-svg notshow" >
          <svg width="22" height="91" viewBox="0 0 22 91" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M1 1L21 23.5V91" stroke="#FFC700" stroke-width="2"/>
          </svg>

        </div>
        <div class="choose-subtitle subtitle notshow" v-html="wpData.choose_subtitle"></div>
        <div class="choose-text text notshow" v-html="wpData.choose_text">

        </div>

      </section>
      <section class="services slide slide__4">
        <div class="services-left notshow">
          <div class="services-subtitle subtitle" >OUR SERVICES</div>
          <div class="services-svg-wrapper">
            <svg class="services-svg" width="24" height="101" viewBox="0 0 24 101" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path d="M1 1L22.2766 26V101" stroke="#FFC700" stroke-width="2"/>
            </svg>
            <div class="services-items">
              <div class="services-items-wrapper">
                <div @click="animateSlideByClick(4, $event)" class="services-item  services-item__restorfx">RESTOR FX</div>
                <div @click="animateSlideByClick(5, $event)" class="services-item services-item__clearfx">CLEAR FX</div>
                <div @click="animateSlideByClick(6, $event)" class="services-item services-item__pdr">P.D.R.</div>
                <div @click="animateSlideByClick(7, $event)" class="services-item services-item__ppf">PPF</div>
                <div @click="animateSlideByClick(8, $event)" class="services-item services-item__dynoflex ">DYNOFLEX</div>
              </div>

            </div>

          </div>
          <div class="services-text-wrapper">

          <p class="services-text services-text__restorfx text" v-html="wpData.restorfx_text"></p>
          <p class="services-text services-text__clearfx notshow text" v-html="wpData.clearfx_text"></p>
          <p class="services-text services-text__pdr notshow text" v-html="wpData.pdr_text"></p>
          <p class="services-text services-text__ppf notshow text" v-html="wpData.ppf_text"></p>
          <p class="services-text services-text__dynoflex notshow text" v-html="wpData.dynoflex_text"></p>
          </div>
          <PrimaryButton class="services-button" @click="showPopup = true">Get in touch</PrimaryButton>
        </div>
        <div class="services-right notshow">
          <div class="services-car car notshow services-car__restorfx">
            <div class="car-images">
              <img class="car-images-image car-images-image__full" src="@/assets/img/car_main/clear_car.png"  alt="Car"/>
              <img :class="'car-images-image car-image ' + service.dataName " :data-serviceImage="service.dataName" v-for="service, i in services_restorfx_services" :key="i" :src="service.image" alt="Car">
            </div>
            <div class="car-services">
              <div :class="`service car-service car-service__restorfx car-service__${service.dataName}`"   v-for="service,i in services_restorfx_services" :key="i" :data-service="service.dataName" @click="hideServiceCarImage(service.dataName, $event, services_restorfx_services)">
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
          <div class="services-car car notshow services-car__clearfx">
            <!-- <img class="services-car__clearfx-under" :src="'./assets/img/services/clearfx_under.png'" alt=""> -->
            <div class="car-images-compare" ref="compare">
              <img :src="services_clearfx_services[1].image" alt="" />
              <img :src="services_clearfx_services[0].image" alt="" />
            </div>

          </div>
          <div class="services-car car notshow services-car__pdr">
            <div class="car-images">
              <img class="car-images-image car-images-image__full" :src="'./assets/img/services/pdr_full.png'"  alt="Car"/>
              <img :class="'car-images-image car-image ' + service.dataName " :data-serviceImage="service.dataName" v-for="service, i in services_pdr_services" :key="i" :src="service.image" alt="Car">
            </div>
            <div class="car-services">
              <div :class="`service car-service car-service__restorfx car-service__${service.dataName}`"   v-for="service,i in services_pdr_services" :key="i" :data-service="service.dataName" @click="hideServiceCarImage(service.dataName, $event, services_pdr_services)">
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
          <div class="services-car car notshow services-car__ppf">
            <div class="car-images">
              <img class="car-images-image car-images-image__full" :src="'./assets/img/services/ppf_full.png'"  alt="Car"/>
            </div>
          </div>
          <div class="services-car car notshow services-car__dynoflex">
            <div class="car-images">
              <img class="car-images-image car-images-image__full" :src="'./assets/img/services/dynoflex_full.png'"  alt="Car"/>
              <img :class="'car-images-image car-image ' + service.dataName " :data-serviceImage="service.dataName" v-for="service, i in services_dynoflex_services" :key="i" :src="service.image" alt="Car">
            </div>
            <div class="car-services">
              <div :class="`service car-service car-service__restorfx car-service__${service.dataName}`"   v-for="service,i in services_dynoflex_services" :key="i" :data-service="service.dataName" @click="hideServiceCarImage(service.dataName, $event, services_dynoflex_services)">
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

        </div>
        <Features class="services-features services-features__restorfx " :features="wpData.restorfx_features"></Features>
        <Features class="services-features services-features__clearfx " :features="wpData.clearfx_features"></Features>
        <Features class="services-features services-features__pdr " :features="wpData.pdr_features"></Features>
        <Features class="services-features services-features__ppf " :features="wpData.ppf_features"></Features>
        <Features class="services-features services-features__dynoflex " :features="wpData.dynoflex_features"></Features>

      </section>
      <section class="feedback slide slide__5">
        <div class="feedback-left">
          <div class="feedback-subtitle subtitle" v-html="wpData.feedback_subtitle"></div>
          <div class="feedback-arrows">
            <button class="feedback-arrows-item feedback-arrows-item__left">
              <svg width="52" height="24" viewBox="0 0 52 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M14.3593 23.4348L16.6997 21.5344L6.32012 13.0633L51.8911 13.0633L51.8911 10.3715L6.32012 10.3715L16.6997 1.90044L14.3593 2.91438e-05L-0.00018971 11.7174L14.3593 23.4348Z" fill="#FFC700"/>
              </svg>
            </button>
            <button class="feedback-arrows-item feedback-arrows-item__right">
              <svg width="52" height="24" viewBox="0 0 52 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M37.6407 0.000244141L35.3003 1.90065L45.6799 10.3717H0.108887V13.0635H45.6799L35.3003 21.5346L37.6407 23.435L52.0002 11.7176L37.6407 0.000244141Z" fill="#FFC700"/>
              </svg>
            </button>
          </div>
          <div class="feedback-title title" v-html="wpData.feedback_title"></div>
          <!-- <div class="feedback-text text" v-html="wpData.feedback_text"></div> -->
          <PrimaryButton @click="showPopup = true">Get in touch</PrimaryButton>
        </div>
        <div class="feedback-right">
          <!-- <div class="feedback-certificates">
            <swiper class="swiper feedback-certificates-slider" :slides-per-view="'auto'" :space-between="83" :modules="modules" :breakpoints="certificatesSliderSwiperBreakpoints">
              <swiper-slide v-for="cert, i in wpData.feedback_certificates" :key="i" class="feedback-certificates-slide">

                <img :src="cert.image.url" alt="Certificate">

              </swiper-slide>


            </swiper>
          </div> -->
          <div class="feedback-reviews">
            <swiper class="swiper feedback-reviews-slider" :slides-per-view="'2'" :space-between="76" :modules="modules" :navigation="{nextEl: '.feedback-arrows-item__right', prevEl: '.feedback-arrows-item__left'}" >
              <swiper-slide v-for="review, i in desktopReviewsSlider" :key="i" class="feedback-reviews-slide">
                <div class="feedback-reviews-item">

                  <svg class="feedback-reviews-slide-svg" width="12" height="48" viewBox="0 0 12 48" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M1 1L11 12.75V48" stroke="#FFC700" stroke-width="2"/>
                  </svg>
                  <div class="feedback-reviews-slide-service">{{ review.service1 }}</div>
                  <div class="feedback-reviews-slide-name">{{ review.name1 }}</div>
                  <p class="feedback-reviews-slide-text text">{{ review.text1 }}</p>
                </div>
                <div class="feedback-reviews-item">

                  <svg class="feedback-reviews-slide-svg" width="12" height="48" viewBox="0 0 12 48" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M1 1L11 12.75V48" stroke="#FFC700" stroke-width="2"/>
                  </svg>
                  <div class="feedback-reviews-slide-service">{{ review.service2 }}</div>
                  <div class="feedback-reviews-slide-name">{{ review.name2 }}</div>
                  <p class="feedback-reviews-slide-text text">{{ review.text2 }}</p>
                </div>
              </swiper-slide>
            </swiper>
          </div>
          <a target="_blank" href="https://www.google.com/maps/place/Xtreme+Performance+PDR/@41.97736,-87.9654348,18z/data=!4m16!1m8!3m7!1s0x880fb34f67a5c353:0x9a64d1adfbee0059!2sXtreme+Performance+PDR!8m2!3d41.9770496!4d-87.9649508!9m1!1b1!3m6!1s0x880fb34f67a5c353:0x9a64d1adfbee0059!8m2!3d41.9770496!4d-87.9649508!9m1!1b1" class="feedback-link yellow-link">All reviews you can see on google maps</a>
        </div>
      </section>
      <section class="map slide slide__6">
        <div class="map-left">
          <h3 class="map-subtitle subtitle" v-html="wpData.map_subtitle"></h3>
          <div class="map-link yellow-link" v-html="wpData.map_address"></div>
          <h2 class="map-title title" v-html="wpData.map_title"></h2>
          <!-- <p class="map-text text" v-html="wpData.map_text"></p> -->
          <PrimaryButton @click="showPopup = true">Get in touch</PrimaryButton>
        </div>
        <div class="map-right google_map" id="google_map">
          <!-- <img alt="map" :src="'./assets/img/map/desktop_map.png'" class="map-image"> -->
          <iframe src="https://www.google.com/maps/embed?pb=!1m14!1m8!1m3!1d189829.2467482208!2d-88.2451022!3d41.9770496!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x880fb387b96d7581%3A0xd4823f114f3e709e!2sRestorFX%20Wood%20Dale!5e0!3m2!1sru!2sru!4v1657913700231!5m2!1sen!2sru&language=iw" width="800" height="600" style="border:0;" allowfullscreen="" loading="lazy" referrerpolicy="no-referrer-when-downgrade"></iframe>
        </div>
        <Features class="map-features" :features="wpData.map_features"></Features>
      </section>
      <section class="contacts slide slide__7">
        <div class="contacts-left">

          <div class="contacts-subtitle subtitle" v-html="wpData.contacts_subtitle"></div>
          <p class="contacts-text text">You have questions? Please leave your phone number in the form below and our manager will contact you to answer them!</p>
          <RestorForm class="contacts-form"></RestorForm>
          <div class="contacts-rights footer-item">Restor FX 2022 © ALL RIGHTS RESERVED.</div>
        </div>

        <div class="contacts-right">
          <div class="contacts-wrapper">
            <div class="contacts-col contacts-phones">
              <div class="contacts-item-title">
                CALL CENTRE
              </div>
              <div class="contacts-item-items">
                <a :href="`tel:${phone.number}`" v-for="phone,i in wpData.contacts_phones" :key="i">
                  <img :src="'./assets/img/contacts/bg.png'">{{phone.number}}</a>
              </div>
            </div>
            <div class="contacts-col contacts-social">
              <div class="contacts-item">
                <div class="contacts-item-title">SOCIAL NETWORKS</div>
                <div class="contacts-item-items">
                  <a :href="wpData.contacts_inst">
                    <img :src="'./assets/img/contacts/soc-bg.png'">
                    INSTAGRAM</a>
                  <a :href="wpData.contacts_fb">
                    <img :src="'./assets/img/contacts/soc-bg.png'">
                    FACEBOOK</a>
                </div>
              </div>
              <div class="contacts-item">
                <div class="contacts-item-title">Messenger</div>
                <div class="contacts-item-items">
                  <a :href="wpData.contacts_wa">
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
                <a :href="`mailto:${wpData.contacts_email}`">{{wpData.contacts_email}}</a>
              </div>
            </div>
          </div>
          <div class="contacts-footer">
            <a href="#" class="footer-item contacts-privacy">TERMS OF PRIVACY POLICY</a>
            <a href="https://stlgv.com/" class="contacts-dev footer-item footer-item__yellow">
              <div class="contacts-dev-left">PREMIUM WEBSITE DEVELOPMENT:</div>
              <div class="contacts-dev-logo">
                <img :src="'./assets/img/footer/desktop_dev_logo.png'" alt="DevTeam">
              </div>
            </a>
          </div>
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
          <NavBar class="header-navbar"></NavBar>
          <Phone class="header-phone" :tel="tel"></Phone>
          <!-- <Gamb class="header-gamb" @click="showMenu = true" :class="{active: showMenu}"></Gamb> -->
          <button class="header-menu" @click="showMenu = true">
             <svg width="22" height="11" viewBox="0 0 22 11" fill="none" xmlns="http://www.w3.org/2000/svg">
              <rect x="0.211914" width="21" height="2" fill="#050502"/>
              <rect x="0.211914" y="9" width="21" height="2" fill="#050502"/>
            </svg>

          </button>



        </div>
      </header>
      <div v-sticky class="header fixed-header">
        <div class="header-wrapper">
          <Logo class="header-logo"/>
          <Map class="header-map"/>
          <NavBar class="header-navbar"></NavBar>
          <Phone class="header-phone" :tel="tel"></Phone>
          <!-- <Gamb class="header-gamb" @click="showMenu = true" :class="{active: showMenu}"></Gamb> -->
          <button class="header-menu" @click="showMenu = true">
             <svg width="22" height="11" viewBox="0 0 22 11" fill="none" xmlns="http://www.w3.org/2000/svg">
              <rect x="0.211914" width="21" height="2" fill="#050502"/>
              <rect x="0.211914" y="9" width="21" height="2" fill="#050502"/>
            </svg>

          </button>

        </div>
      </div>
      <section class="offer">
        <div class="offer-subtitle subtitle" v-html="wpData.offer_subtitle"></div>
        <h1 class="offer-title title" v-html="wpData.offer_title"></h1>
        <p class="offer-text text" v-html="wpData.offer_text"></p>
        <MobileButton @click="showPopup = true"   class="offer-btn offer-btn__mobile">Get in touch</MobileButton>
        <PrimaryButton @click="showPopup = true" class="offer-btn offer-btn__desktop">Get in touch</PrimaryButton>
        <Tesla class="offer-car"></Tesla>
        <Features class="offer-features" :features="wpData.offer_features"></Features>
      </section>
      <section ref="mobileAbout" id="about"  class="about">
        <div class="about-subtitle subtitle" v-html="wpData.about_subtitle"></div>
        <h2 class="about-title title" v-html="wpData.about_title"></h2>
        <div class="about-text text">
          <p class="about-text__1" v-html="wpData.about_text_1"></p>
          <p class="about-text__2 text-shortened" v-html="wpData.about_text_2"></p>

        </div>
        <div class="about-video" @click="showVideo = true">
          <div class="about-video-text">
            <svg width="50" height="50" viewBox="0 0 50 50" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path d="M21.6216 18.9189L31.7567 25L21.6216 31.0811V18.9189Z" fill="white"/>
              <circle cx="25" cy="25" r="24.3243" stroke="#FFC700" stroke-width="1.35135"/>
            </svg>
            <span>WATCH VIDEO PRESENTATION</span>
          </div>
        </div>
        <div class="about-image">
          <img :src="'./assets/img/about/about-mobile-bg.png'" data-works alt="About">
        </div>
      </section>
      <section class="choose">
        <div class="choose-wrapper">
          <div class="choose-subtitle subtitle" v-html="wpData.choose_subtitle"></div>
          <div class="choose-text text" v-html="wpData.choose_text">

          </div>
        </div>
        <div class="choose-car">
          <img :src="'./assets/img/choose/car.png'" alt="Tesla">
        </div>

        <MobileButton @click="showPopup = true"  class="choose-btn">Get in touch</MobileButton>
      </section>
      <section id="services" class="services">
        <h2 class="services-subtitle subtitle">OUR SERVICES</h2>
        <div class="services-slider">
          <div class="services-slider-navi">
            <button class="services-slider-arrow services-slider-arrow__left">
              <svg width="52" height="24" viewBox="0 0 52 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M14.3593 23.4348L16.6997 21.5344L6.32012 13.0633L51.8911 13.0633L51.8911 10.3715L6.32012 10.3715L16.6997 1.90044L14.3593 2.91438e-05L-0.00018971 11.7174L14.3593 23.4348Z" fill="#FFC700"/>
              </svg>
            </button>
            <button class="services-slider-arrow services-slider-arrow__right">
              <svg width="52" height="24" viewBox="0 0 52 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M37.6407 0.000244141L35.3003 1.90065L45.6799 10.3717H0.108887V13.0635H45.6799L35.3003 21.5346L37.6407 23.435L52.0002 11.7176L37.6407 0.000244141Z" fill="#FFC700"/>
              </svg>
            </button>
          </div>
          <swiper class="swiper services-slider" :space-between="50" :allow-touch-move="false" :slides-per-view="1"  :modules="modules" :navigation="{nextEl: '.services-slider-arrow__right', prevEl: '.services-slider-arrow__left'}" >
            <!-- <div> -->
            <swiper-slide  class="slide services-slide services-slide__restorfx">
              <div class="services-slide-title">
                Restor fx
              </div>
              <p class="services-slide-text text">{{wpData.restorfx_text}}</p>
              <div class="services-car car  services-car__restorfx">
                <div class="car-images">
                  <img class="car-images-image car-images-image__full" src="@/assets/img/car_main/clear_car.png"  alt="Car"/>
                  <img :class="'car-images-image car-image ' + service.dataName " :data-serviceImage="service.dataName" v-for="service, i in services_restorfx_services" :key="i" :src="service.image" alt="Car">
                </div>
                <div class="car-services">
                  <div :class="`service car-service car-service__restorfx car-service__${service.dataName}`"   v-for="service,i in services_restorfx_services" :key="i" :data-service="service.dataName" @click="hideServiceCarImage(service.dataName, $event, services_restorfx_services)">
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
              <Features class="services-slide-features" :features="wpData.restorfx_features"></Features>
            </swiper-slide>
            <swiper-slide  class="slide services-slide services-slide__clearfx">
              <div class="services-slide-title">
                Clearfx
              </div>
              <p class="services-slide-text text">{{wpData.clearfx_text}}</p>
              <div class="services-car car  services-car__clearfx">
                <!-- <img class="services-car__clearfx-under" :src="'./assets/img/services/clearfx_under.png'" alt=""> -->
                <div class="car-images-compare" ref="mobilecompare">
                  <img :src="services_clearfx_services[1].image" alt="" />
                  <img :src="services_clearfx_services[0].image" alt="" />
                </div>

              </div>
              <Features class="services-slide-features" :features="wpData.clearfx_features"></Features>
            </swiper-slide>
            <swiper-slide  class="slide services-slide services-slide__pdr">
              <div class="services-slide-title">
                Pdr
              </div>
              <p class="services-slide-text text">{{wpData.pdr_text}}</p>
              <div class="services-car car  services-car__pdr">
                <div class="car-images">
                  <img class="car-images-image car-images-image__full" :src="'./assets/img/services/pdr_full.png'"  alt="Car"/>
                  <img :class="'car-images-image car-image ' + service.dataName " :data-serviceImage="service.dataName" v-for="service, i in services_pdr_services" :key="i" :src="service.image" alt="Car">
                </div>
                <div class="car-services">
                  <div :class="`service car-service car-service__restorfx car-service__${service.dataName}`"   v-for="service,i in services_pdr_services" :key="i" :data-service="service.dataName" @click="hideServiceCarImage(service.dataName, $event, services_pdr_services)">
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
              <Features class="services-slide-features" :features="wpData.pdr_features"></Features>
            </swiper-slide>
            <swiper-slide  class="slide services-slide services-slide__ppf">
              <div class="services-slide-title">
                ppf
              </div>
              <p class="services-slide-text text">{{wpData.ppf_text}}</p>
              <div class="services-car car  services-car__ppf">
                <div class="car-images">
                  <img class="car-images-image car-images-image__full" :src="'./assets/img/services/ppf_full.png'"  alt="Car"/>
                </div>
              </div>
              <Features class="services-slide-features" :features="wpData.ppf_features"></Features>
            </swiper-slide>
            <swiper-slide  class="slide services-slide services-slide__dynoflex">
              <div class="services-slide-title">
                Dynoflex
              </div>
              <p class="services-slide-text text">{{wpData.dynoflex_text}}</p>
              <div class="services-car car  services-car__dynoflex">
                <div class="car-images">
                  <img class="car-images-image car-images-image__full" :src="'./assets/img/services/dynoflex_full.png'"  alt="Car"/>
                  <img :class="'car-images-image car-image ' + service.dataName " :data-serviceImage="service.dataName" v-for="service, i in services_dynoflex_services" :key="i" :src="service.image" alt="Car">
                </div>
                <div class="car-services">
                  <div :class="`service car-service car-service__restorfx car-service__${service.dataName}`"   v-for="service,i in services_dynoflex_services" :key="i" :data-service="service.dataName" @click="hideServiceCarImage(service.dataName, $event, services_dynoflex_services)">
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
              <Features class="services-slide-features" :features="wpData.dynoflex_features"></Features>
            </swiper-slide>
            <!-- </div> -->
          </swiper>

        </div>
        <MobileButton @click="showPopup = true"  class="services-btn">Get in touch</MobileButton>
      </section>
      <section class="feedback"  id="reviews">
        <div class="feedback-subtitle subtitle">
          <svg width="16" height="63" viewBox="0 0 16 63" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M1 1L14.6546 16.3614V62.4458" stroke="#FFC700" stroke-width="1.36546"/>
          </svg>
          Feedback</div>
        <h2 class="feedback-title title">customer<br>reviews</h2>
        <!-- <p class="feedback-text text">{{wpData.feedback_text}}</p> -->
        <MobileButton @click="showPopup = true"  class="feedback-btn">Get in touch</MobileButton>
        <!-- <div class="feedback-certificates">

          <swiper class="swiper feedback-certificates-slider" :modules="modules" :slides-per-view="'auto'" :space-between="40">
            <swiper-slide v-for="cert, i in wpData.feedback_certificates" :key="i" class="slide feedback-certificates-slide">
              <img :src="cert.image.url" alt="Certificate">
            </swiper-slide>
          </swiper>
        </div> -->
        <div class="feedback-inbetween">
          <a target="_blank" href="https://www.google.com/maps/place/Xtreme+Performance+PDR/@41.97736,-87.9654348,18z/data=!4m16!1m8!3m7!1s0x880fb34f67a5c353:0x9a64d1adfbee0059!2sXtreme+Performance+PDR!8m2!3d41.9770496!4d-87.9649508!9m1!1b1!3m6!1s0x880fb34f67a5c353:0x9a64d1adfbee0059!8m2!3d41.9770496!4d-87.9649508!9m1!1b1" class="yellow-link feedback-inbetween-google">All reviews you can<br>see on google maps</a>
          <div class="feedback-slider-navi">
            <button class="feedback-slider-arrow feedback-slider-arrow__left">
              <svg width="36" height="17" viewBox="0 0 36 17" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M9.88371 16.1304L11.4946 14.8223L4.35022 8.99155L35.7173 8.99155L35.7173 7.13875L4.35022 7.13875L11.4946 1.308L9.88371 -7.47377e-05L-0.00012518 8.06515L9.88371 16.1304Z" fill="#FFC700"/>
              </svg>

            </button>
            <button class="feedback-slider-arrow feedback-slider-arrow__right">
              <svg width="36" height="17" viewBox="0 0 36 17" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M26.1163 0L24.5054 1.30807L31.6498 7.13882H0.282715V8.99162H31.6498L24.5054 14.8224L26.1163 16.1304L36.0001 8.06522L26.1163 0Z" fill="#FFC700"/>
              </svg>

            </button>
          </div>
        </div>
        <div class="feedback-reviews">
          <swiper class="swiper feedback-reviews-slider" :slides-per-view="'auto'" :space-between="40" :modules="modules" :navigation="{nextEl: '.feedback-slider-arrow__right', prevEl: '.feedback-slider-arrow__left'}" >
            <swiper-slide v-for="review, i in wpData.feedback_reviews" :key="i" class="feedback-reviews-slide">

              <svg class="feedback-reviews-slide-svg" width="12" height="48" viewBox="0 0 12 48" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M1 1L11 12.75V48" stroke="#FFC700" stroke-width="2"/>
              </svg>
              <div class="feedback-reviews-slide-service">{{ review.service }}</div>
              <div class="feedback-reviews-slide-name">{{ review.name }}</div>
              <p class="feedback-reviews-slide-text text">{{ review.text }}</p>
            </swiper-slide>
          </swiper>
        </div>
      </section>
      <section id="map" class="map">
        <div class="map-subtitle subtitle">
            <svg width="22" height="92" viewBox="0 0 22 92" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M1 1.37891L21 23.8789V91.3789" stroke="#FFC700" stroke-width="2"/>
            </svg>
            <span v-html="wpData.map_subtitle"></span>
          </div>
        <h2 class="map-title title" v-html="wpData.map_title"></h2>
        <!-- <p class="map-text text">{{wpData.map_text}}</p> -->
        <MobileButton @click="showPopup = true"  class="map-button">Get in touch</MobileButton>
        <div class="yellow-link map-link">735 N EDGEWOOD AVE,<br>UNIT F WOOD DALE</div>
        <div class="map-map">
          <!-- <img  :src="'./assets/img/map/map.png'" alt="Map"> -->
          <iframe src="https://www.google.com/maps/embed?pb=!1m14!1m8!1m3!1d189829.2467482208!2d-88.2451022!3d41.9770496!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x880fb387b96d7581%3A0xd4823f114f3e709e!2sRestorFX%20Wood%20Dale!5e0!3m2!1sru!2sru!4v1657265207875!5m2!1sen!2sru&language=iw" width="600" height="450" style="border:0;" allowfullscreen="" loading="lazy" referrerpolicy="no-referrer-when-downgrade"></iframe>
        </div>
      </section>
      <section class="contact">
          <div class="contact-subtitle subtitle">{{wpData.contacts_subtitle}}</div>
          <p class="contact-text text">You have questions? Please leave your phone number in the form below and our manager will contact you to answer them!</p>


          <RestorForm class="contact-form"></RestorForm>
          <div class="contact-blocks"  id="contact">
            <div class="contact-centers contact-block">
              <div class="contact-block-title">CALL CENTRE</div>
              <div class="contact-block-items">
                <a v-for="phone, i in wpData.contacts_phones" :href="`tel:${phone.number}`" :key="i">{{phone.number}}</a>

              </div>
            </div>
            <div class="contact-socials contact-block">
              <div class=" contact-block-title">SOCIAL NETWORKS</div>
              <div class="contact-block-items">
                <a :href="wpData.contacts_inst">INSTAGRAM</a>
                <a :href="wpData.contacts_fb">FACEBOOK</a>
                <a :href="wpData.contacts_wa">WHATSAPP</a>

              </div>
            </div>
          </div>
          <div class="contact-email contact-block">
            <div class="contact-block-title">E-mail</div>

            <a class="mobile" :href="`mailto:${wpData.contacts_email}`">info@restorfx<br>wooddale.com</a>
            <a class="tablet" :href="`mailto:${wpData.contacts_email}`">{{wpData.contacts_email}}</a>
          </div>
      </section>
      <footer class="footer">
        <div class="footer-item footer-rights">
          <span>Restor FX 2022 © ALL RIGHTS RESERVED.</span>
        </div>
        <div class="footer-item footer-policy">
          <a href="#">TERMS OF PRIVACY POLICY</a>
        </div>
        <a href="https://stlgv.com/" class="footer-item footer-dev">
          <span>PREMIUM WEBSITE DEVELOPMENT:</span>
          <span><img :src="'./assets/img/footer/footer-dev.png'" alt="Site Development Logo"></span>
        </a>
      </footer>
      <a :href="wpData.contacts_wa" class="wa-link">
        <svg width="58" height="58" viewBox="0 0 58 58" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M29 58C45.0162 58 58 45.0162 58 29C58 12.9838 45.0162 0 29 0C12.9838 0 0 12.9838 0 29C0 45.0162 12.9838 58 29 58Z" fill="#25D366"/>
        <path fill-rule="evenodd" clip-rule="evenodd" d="M29.9559 45.1343H29.9488C27.0627 45.1333 24.2268 44.4091 21.7081 43.0353L12.5667 45.4333L15.013 36.4974C13.504 33.8823 12.71 30.9158 12.7112 27.8765C12.715 18.3687 20.4508 10.6333 29.9557 10.6333C34.5687 10.6353 38.8984 12.4312 42.1541 15.6907C45.4099 18.95 47.2018 23.2825 47.2 27.8901C47.1963 37.3958 39.4635 45.1304 29.9559 45.1343ZM22.1317 39.9135L22.655 40.2241C24.8556 41.53 27.3782 42.221 29.9501 42.2219H29.9559C37.8556 42.2219 44.2853 35.7921 44.2884 27.8892C44.29 24.0593 42.8006 20.4584 40.0945 17.7492C37.3885 15.04 33.7898 13.5472 29.9615 13.5459C22.0556 13.5459 15.6259 19.9751 15.6228 27.8776C15.6217 30.5858 16.3794 33.2232 17.8141 35.5052L18.155 36.0475L16.707 41.3365L22.1317 39.9135ZM38.0533 31.6027C38.3538 31.748 38.5568 31.8461 38.6435 31.9907C38.7511 32.1704 38.7511 33.0332 38.3922 34.0397C38.033 35.0462 36.3116 35.9648 35.4838 36.0884C34.7415 36.1995 33.802 36.2458 32.7699 35.9177C32.1441 35.7192 31.3416 35.4541 30.3136 35.0101C26.2742 33.2659 23.5444 29.3509 23.0284 28.6109C22.9923 28.5591 22.967 28.5228 22.9529 28.504L22.9495 28.4994C22.7215 28.1951 21.1935 26.1565 21.1935 24.0468C21.1935 22.062 22.1684 21.0217 22.6172 20.5429C22.648 20.5101 22.6763 20.4799 22.7015 20.4522C23.0966 20.0209 23.5633 19.913 23.8506 19.913C24.1378 19.913 24.4254 19.9156 24.6764 19.9283C24.7074 19.9299 24.7396 19.9296 24.7729 19.9294C25.024 19.9279 25.337 19.9261 25.6459 20.6679C25.7647 20.9533 25.9386 21.3766 26.1219 21.823C26.4926 22.7256 26.9023 23.7229 26.9743 23.8672C27.0821 24.0829 27.1539 24.3345 27.0102 24.6221C26.9887 24.6652 26.9688 24.7059 26.9497 24.7448C26.8418 24.9651 26.7625 25.127 26.5793 25.3409C26.5074 25.4249 26.433 25.5155 26.3586 25.6061C26.2103 25.7867 26.0622 25.9672 25.9331 26.0958C25.7173 26.3106 25.4928 26.5437 25.7441 26.9751C25.9955 27.4064 26.8603 28.8174 28.1411 29.96C29.5181 31.1882 30.7149 31.7073 31.3214 31.9703C31.4399 32.0218 31.5358 32.0633 31.6062 32.0986C32.0369 32.3143 32.2882 32.2782 32.5397 31.9907C32.791 31.7031 33.6168 30.7325 33.9039 30.3012C34.1911 29.8701 34.4784 29.9419 34.8733 30.0855C35.2685 30.2296 37.3868 31.2718 37.8177 31.4875C37.9018 31.5295 37.9804 31.5676 38.0533 31.6027Z" fill="#FDFDFD"/>
        </svg>

      </a>
    </div>
    <transition name="slideout">
      <div class="preloader" v-show="!isFetching" >
        <Logo class="preloader-logo"></Logo>
        <div class="preloader-wrapper">
          <div class="preloader-text">Loading..</div>
          <div class="preloader-percent">0</div>
        </div>
        <div class="preloader-line">
          <div class="prealoader-line-current"></div>
        </div>
      </div>
    </transition>
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
            <div class="popup-subtitle subtitle">GET IN TOUCH<br>WITH US</div>
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
                    <a :href="`tel:${phone.number}`" v-for="phone,i in wpData.contacts_phones" :key="i">
                      <img :src="'./assets/img/contacts/bg.png'">{{phone.number}}</a>
                  </div>
                </div>
                <div class="contacts-col contacts-social">
                  <div class="contacts-item">
                    <div class="contacts-item-title">SOCIAL NETWORKS</div>
                    <div class="contacts-item-items">
                      <a :href="wpData.contacts_inst">
                        <img :src="'./assets/img/contacts/soc-bg.png'">
                        INSTAGRAM</a>
                      <a :href="wpData.contacts_fb">
                        <img :src="'./assets/img/contacts/soc-bg.png'">
                        FACEBOOK</a>
                    </div>
                  </div>
                  <div class="contacts-item">
                    <div class="contacts-item-title">Messenger</div>
                    <div class="contacts-item-items">
                      <a :href="wpData.contacts_wa">
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
                    <a :href="`mailto:${wpData.contacts_email}`">{{wpData.contacts_email}}</a>
                  </div>
                </div>
              </div>
            </div>

          </div>
        </div>
      </div>
    </transition>
    <transition name="fadeIn">
      <div class="video" @click="hideVideo($event)" v-show="showVideo">
        <div class="video-block">
          <iframe width="760" height="415" src="https://www.youtube.com/embed/UvqOZHumTr8" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
        </div>
      </div>
    </transition>
  </div>

</template>

<script>
  import gsap from "gsap";
  import { Navigation } from 'swiper'
  import ImageCompare from "image-compare-viewer";

  import { Swiper, SwiperSlide } from 'swiper/vue/swiper-vue';
  import {Form, Field, ErrorMessage} from 'vee-validate'
  import 'swiper/swiper-bundle.min.css'
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

export default {
  name: "Home",
  setup() {
    return {
      modules: [Navigation],
    }
  },
  components: {
    PrimaryButton,
    Features,
    Car,
    Tesla,
    MobileButton,
    Swiper,
    SwiperSlide,
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
    wpData: {


    "offer_features": {
        "feauture_1": {
            "subtitle": "Restoration",
            "title": "Restor FX"
        },
        "feauture_2": {
            "subtitle": "Paintless",
            "title": "DENT REPAIR"
        },
        "feauture_3": {
            "subtitle": "Creamic Coat",
            "title": "CLEAR FX"
        }
    },
    "restorfx_features": {
        "feauture_1": {
            "subtitle": "The Cover Will Shine",
            "title": "Restores paint"
        },
        "feauture_2": {
            "subtitle": "Doesn't Wash Off",
            "title": "Eternal Coverage"
        },
        "feauture_3": {
            "subtitle": "Additional UV Protection",
            "title": "100% Protection"
        }
    },
    "pdr_features": {
        "feauture_1": {
            "subtitle": "Cheaper Method",
            "title": "Affordable"
        },
        "feauture_2": {
            "subtitle": "Retaining Factory Finish",
            "title": "Boosts Resale Value"
        },
        "feauture_3": {
            "subtitle": "It's Faster",
            "title": "Quick Solution"
        }
    },

    "ppf_features": {
        "feauture_1": {
            "subtitle": "Retains Paint",
            "title": "Keeps Color"
        },
        "feauture_2": {
            "subtitle": "Saves From Rocks and Hail",
            "title": "Extra Protection"
        },
        "feauture_3": {
            "subtitle": "Reliable Coverage",
            "title": "Long-Lasting"
        }
    },


    "map_features": {
        "feauture_1": {
            "subtitle": "Restavration",
            "title": "RESTOR FX"
        },
        "feauture_2": {
            "subtitle": "Upgrades",
            "title": "VEHICLE APPEARANCE"
        },
        "feauture_3": {
            "subtitle": "Repair",
            "title": "DINGS & DENTS"
        }
    },
    "clearfx_features": {
        "feauture_1": {
            "subtitle": "Best Performance",
            "title": "Brilliant Shine"
        },
        "feauture_2": {
            "subtitle": "No Scratches or Dirt",
            "title": "Powerful protection"
        },
        "feauture_3": {
            "subtitle": "Repels Dirty Drops",
            "title": "Hydrophobicity"
        }
    },
    "dynoflex_features": {
        "feauture_1": {
            "subtitle": "Saves Windshields",
            "title": "Chip Protection"
        },
        "feauture_2": {
            "subtitle": "Drip Protection",
            "title": "Anti-Rain Effect"
        },
        "feauture_3": {
            "subtitle": "Stored For a Long Time",
            "title": "Chemical Resistance"
        }
    }

    },
    isFetching: true,
    prevSlide: null,
    currentSlide: 1,
    canAnimateSlide: true,
    tel: '(708) 887 99 88',
    services_restorfx_services: [
      {
        title: 'RestorFX',
        subtitle: 'Some Text Test',
        dataName: 'restorfx_1',
        image: './assets/img/services/restorfx_1.png',
        isShowing: true

      },
      {
        title: 'RestorFX',
        subtitle: 'Some Text Test',
        dataName: 'restorfx_2',
        image: './assets/img/services/restorfx_2.png',
        isShowing: true

      }

    ],
    services_clearfx_services: [
      {
        dataName: 'clearfx',
        image: './assets/img/services/clearfx_dirty.png',
        zIndex: 6,
        isShowing: true,
      },
      {
        dataName: 'dynoflex',
        image: './assets/img/services/clearfx_clear.png',
        zIndex: 6,
        isShowing: true,
      },

    ],
    services_pdr_services: [
      {
        title: 'Dent Repair',
        subtitle: 'Some test text',
        dataName: 'pdr_1',
        image: './assets/img/services/pdr_1.png',
        zIndex: 6,
        isShowing: true,

      },
      {
        title: 'Dent Repair',
        subtitle: 'Some test text',
        dataName: 'pdr_2',
        image: './assets/img/services/pdr_2.png',
        zIndex: 6,
        isShowing: true,

      },
      {
        title: 'Dent Repair',
        subtitle: 'Some test text',
        dataName: 'pdr_3',
        image: './assets/img/services/pdr_3.png',
        zIndex: 6,
        isShowing: true,

      },

    ],

    services_dynoflex_services: [
      {
        title: 'Dynoflex',
        subtitle: 'Ceramic Coat',
        dataName: 'dynoflex_1',
        image: './assets/img/services/dynoflex_2.png',
        zIndex: 6,
        isShowing: true,

      },
      {
        title: 'DYNOFLEX',
        subtitle: 'Glass Protection',
        dataName: 'dynoflex_2',
        image: './assets/img/services/dynoflex_1.png',
        zIndex: 6,
        isShowing: true,

      },
    ],
    services_restorfx_features: [
      {
        title: "RESTORES PAINT",
        subtitle: "The Cover Will Shine",
      },
      {
        title: "ETERNAL COVERAGE",
        subtitle: "Doesn’t Wash Off",
      },
      {
        title: "100% PROTECTION",
        subtitle: "Additional UV Protection",
      },
    ],
    services_clearfx_features: [
      {
        title: "BRILLIANT SHINE",
        subtitle: "Best Performance",
      },
      {
        title: "POWERFUL PROTECTION",
        subtitle: "No Scratches or Dirt",
      },
      {
        title: "HIDROPHOBICITY",
        subtitle: "Repels Dirty Drops",
      },
    ],
    services_pdr_features: [
      {
        title: "AFFORDABLE",
        subtitle: "Cheaper Method",
      },
      {
        title: "BOOSTS RESALE VALUE",
        subtitle: "Retaining Factory Finish",
      },
      {
        title: "QUICK SOLUTION",
        subtitle: "It’s Faster",
      },
    ],
    services_ppf_features: [
      {
        title: "KEEPS COLOR",
        subtitle: "Retains Paint",
      },
      {
        title: "EXTRA PROTECTION",
        subtitle: "Saves from Rocks and Hail",
      },
      {
        title: "LONG-LASTING",
        subtitle: "Reliable Coverage",
      },
    ],
    services_dynoflex_features: [
      {
        title: "chip protection",
        subtitle: "Saves Windshields",
      },
      {
        title: "anti-rain effect",
        subtitle: "Drip Protection",
      },
      {
        title: "chemical resistance",
        subtitle: "Stored for a Long Time",
      },
    ],
    map_features: [
      {
        title: "RESTOR FX",
        subtitle: "Restavration",
      },
      {
        title: "VEHICLE APPEARANCE",
        subtitle: "Upgrades",
      },
      {
        title: "DINGS & DENTS",
        subtitle: "Repair",
      },
    ],
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
    desktopReviewsSlider: [],
    showMenu: false,
    showPopup: false,
    showVideo: false,
    certificatesSliderSwiperBreakpoints: {
      1199: {
        'spaceBetween': 35
      },
      1500: {
        'spaceBetween': 83
      }
    },
  }),
  mounted() {
    new ImageCompare(this.$refs.compare, {
      // controlColor: "#FFFFFF",
      // addCircle: false,
      // addCircleBlur: true,
      smoothing: false,
      hoverStart: false,
      verticalMode: false,
      startingPoint: 50,
      fluidMode: false
    }).mount();
    new ImageCompare(this.$refs.mobilecompare, {
      // controlColor: "#FFFFFF",
      // addCircle: false,
      // addCircleBlur: true,
      smoothing: false,
      hoverStart: false,
      verticalMode: false,
      startingPoint: 50,
      fluidMode: false
    }).mount();


    // this.initMap();
    this.preloaderTl = gsap.timeline({paused: true})
    this.preloaderTl
      // .to('.preloader')

    this.timeline_1_2 = gsap.timeline({paused: true});
      this.timeline_1_4 = gsap.timeline({paused: true});
      this.timeline_1_9 = gsap.timeline({paused: true});
      this.timeline_1_11 = gsap.timeline({paused: true});


      this.timeline_2_1 = gsap.timeline({paused: true});
      this.timeline_2_3 = gsap.timeline({paused: true});
      this.timeline_2_4 = gsap.timeline({paused: true});
      this.timeline_2_9 = gsap.timeline({paused: true});
      this.timeline_2_11 = gsap.timeline({paused: true})



      this.timeline_3_1 = gsap.timeline({paused: true});
      this.timeline_3_2 = gsap.timeline({paused: true});
      this.timeline_3_4 = gsap.timeline({paused: true});
      this.timeline_3_9 = gsap.timeline({paused: true});
      this.timeline_3_11 = gsap.timeline({paused: true});



      this.timeline_4_1 = gsap.timeline({paused: true});
      this.timeline_4_2 = gsap.timeline({paused: true});
      this.timeline_4_3 = gsap.timeline({paused: true});
      this.timeline_4_5 = gsap.timeline({paused: true});
      this.timeline_4_9 = gsap.timeline({paused: true});
      this.timeline_4_11 = gsap.timeline({paused: true});


      this.timeline_5_2 = gsap.timeline({paused: true});
      this.timeline_5_1 = gsap.timeline({paused: true});
      this.timeline_5_4 = gsap.timeline({paused: true});
      this.timeline_5_6 = gsap.timeline({paused: true});
      this.timeline_5_9 = gsap.timeline({paused: true});
      this.timeline_5_11 = gsap.timeline({paused: true});



      this.timeline_6_1 = gsap.timeline({paused: true});
      this.timeline_6_2 = gsap.timeline({paused: true});
      this.timeline_6_4 = gsap.timeline({paused: true});
      this.timeline_6_5 = gsap.timeline({paused: true});
      this.timeline_6_7 = gsap.timeline({paused: true});
      this.timeline_6_9 = gsap.timeline({paused: true});
      this.timeline_6_11 = gsap.timeline({paused: true});


      this.timeline_7_1 = gsap.timeline({paused: true});
      this.timeline_7_2 = gsap.timeline({paused: true});
      this.timeline_7_4 = gsap.timeline({paused: true});
      this.timeline_7_6 = gsap.timeline({paused: true});
      this.timeline_7_8 = gsap.timeline({paused: true});
      this.timeline_7_9 = gsap.timeline({paused: true});
      this.timeline_7_11 = gsap.timeline({paused: true});


      this.timeline_8_1 = gsap.timeline({paused: true});
      this.timeline_8_2 = gsap.timeline({paused: true});
      this.timeline_8_4 = gsap.timeline({paused: true});
      this.timeline_8_7 = gsap.timeline({paused: true});
      this.timeline_8_9 = gsap.timeline({paused: true});
      this.timeline_8_11 = gsap.timeline({paused: true});



      this.timeline_9_1 = gsap.timeline({paused: true}); // From feedback to map (9 to 10)
      this.timeline_9_2 = gsap.timeline({paused: true}); // From feedback to map (9 to 10)
      this.timeline_9_4 = gsap.timeline({paused: true}); // From feedback to map (9 to 10)
      this.timeline_9_8 = gsap.timeline({paused: true}); // From feedback to map (9 to 10)
      this.timeline_9_10 = gsap.timeline({paused: true}); // From feedback to map (9 to 10)
      this.timeline_9_11 = gsap.timeline({paused: true}); // From feedback to map (9 to 10)



      this.timeline_10_1 = gsap.timeline({paused: true}); // From Map to Contacts (10 to 11)
      this.timeline_10_2 = gsap.timeline({paused: true}); // From Map to Contacts (10 to 11)
      this.timeline_10_4 = gsap.timeline({paused: true}); // From Map to Contacts (10 to 11)
      this.timeline_10_9 = gsap.timeline({paused: true}); // From Map to Contacts (10 to 11)
      this.timeline_10_11 = gsap.timeline({paused: true}); // From Map to Contacts (10 to 11)


      this.timeline_11_1 = gsap.timeline({paused: true}); // From Map to Contacts (10 to 11)
      this.timeline_11_2 = gsap.timeline({paused: true}); // From Map to Contacts (10 to 11)
      this.timeline_11_4 = gsap.timeline({paused: true}); // From Map to Contacts (10 to 11)
      this.timeline_11_9 = gsap.timeline({paused: true}); // From Map to Contacts (10 to 11)
      this.timeline_11_10 = gsap.timeline({paused: true}); // From Map to Contacts (10 to 11)

    //SLIDE 1 ANIMATIONS
    this.timeline_1_2

      .set('.home-container .slide__2', {zIndex: 22, autoAlpha: 1})
      .to('.slide .offer-sub', {duration: 1, x: -450, autoAlpha: 0}, '-=1')
      .to('.slide .offer-btn', {duration: 1, y: 250, autoAlpha: 0}, '-=1')
      .to('.slide .offer-title', {duration: 1, x: -250, autoAlpha: 0}, '-=1')
      .to('.slide .offer-text', {duration: 1, x: -55, autoAlpha: 0}, '-=1')
      .to('.home-container .car__tesla .car-services', { duration: 0.5, autoAlpha: 0, ease:'Expo.easeInOut'}, '-=1.5')
      .to('.home-container .offer-features .feature', {stagger: 0.2,duration: 1, y: 100, autoAlpha: 0}, '-=1.5')
      .to('.home-container .car__tesla', {duration: 1.75, xPercent: -136, ease:'Expo.easeInOut'}, '-=1.5')
      .fromTo('.animated__about-subtitle', {autoAlpha: 0, maxWidth: '0px'},{duration: 2, autoAlpha: 1, maxWidth: '220px', ease:'Expo.easeInOut'}, '-=2')
      .fromTo('.animated__about-title', {autoAlpha: 0, maxWidth: '0px'},{duration: 2, autoAlpha: 1, maxWidth: '738px', ease:'Expo.easeInOut'}, '-=2')
      .fromTo('.animated__about-text-1', {autoAlpha: 0, maxWidth: '0px'},{duration: 2, autoAlpha: 1, maxWidth: '383px', ease:'Expo.easeInOut'}, '-=2')
      .fromTo('.animated__about-text-2', {autoAlpha: 0, maxWidth: '0px'},{duration: 2, autoAlpha: 1, maxWidth: '292px', ease:'Expo.easeInOut'}, '-=2')
      .to('.home-container .about-bg', {duration: 1.5, autoAlpha: 1}, '-=1.25')
      .fromTo('.home-container .about-return', {x: 100, autoAlpha: 0},{duration: 1.5, autoAlpha: 1, x: 0}, '-=1.75')
      .set('.home-container .offer', {zIndex: 0})
      .fromTo('.home-container .about-video', {y: 100, autoAlpha: 0},{duration: 1, autoAlpha: 1, y: 0, onComplete: () => {
          this.canAnimateSlide = true
      }}, '-=1.25')

      this.timeline_1_4
        .set('.slide__1', {zIndex: 0})
        // .set('.slide__4', {zIndex: 21})
        .to('.slide .offer-sub', {duration: 1, x: -450, autoAlpha: 0}, '-=1')
        .to('.slide .offer-btn', {duration: 1, y: 250, autoAlpha: 0}, '-=1')
        .to('.slide .offer-title', {duration: 1, x: -250, autoAlpha: 0}, '-=1')
        .to('.slide .offer-text', {duration: 1, x: -55, autoAlpha: 0}, '-=1')
        .to('.home-container .car__tesla .car-services', { duration: 0.5, autoAlpha: 0, ease:'Expo.easeInOut'}, '-=1.5')
        .to('.home-container .offer-features .feature', {stagger: 0.2,duration: 1, y: 100, autoAlpha: 0}, '-=1.5')
        .to('.home-container .car__tesla', {duration: 2.5, xPercent: -250, ease:'Expo.easeInOut'}, '-=1.5')

        .set('.home-container .services-item__restorfx', {scale: 1.5, autoAlpha: 1}, '-=2')
        .to('.home-container .services-left', {duration: 1, autoAlpha: 1}, '-=1')
        .to('.home-container .services-right', {duration: 1, autoAlpha: 1}, '-=1')
        .to('.home-container .services-car__restorfx', {duration: 1, autoAlpha: 1}, '-=1')
        .to('.home-container .services-text__restorfx', {duration: 1, autoAlpha: 1}, '-=1')
        // .to('.home-container .services-item__restorfx', {duration: 1, autoAlpha: 0.2}, '-=1')
        .set('.home-container .services-features__restorfx', {duration: 1, autoAlpha: 1}, '-=1')
        .to('.home-container .services-features__restorfx .feature', {duration: 0.5, stagger: 0.1, autoAlpha: 1, y: -120, onComplete: () => {this.canAnimateSlide = true}}, '-=1')

      this.timeline_1_9
        .set('.slide__1', {zIndex: 0})
        .set('.home-container .feedback', {zIndex: 21})
        .to('.slide .offer-sub', {duration: 1, x: -450, autoAlpha: 0}, '-=1')
        .to('.slide .offer-btn', {duration: 1, y: 250, autoAlpha: 0}, '-=1')
        .to('.slide .offer-title', {duration: 1, x: -250, autoAlpha: 0}, '-=1')
        .to('.slide .offer-text', {duration: 1, x: -55, autoAlpha: 0}, '-=1')
        .to('.home-container .car__tesla .car-services', { duration: 0.5, autoAlpha: 0, ease:'Expo.easeInOut'}, '-=1.5')
        .to('.home-container .offer-features .feature', {stagger: 0.2,duration: 1, y: 100, autoAlpha: 0}, '-=1')
        .to('.home-container .car__tesla', {duration: 2.5, xPercent: -250, ease:'Expo.easeInOut'}, '-=1.5')


        .to('.home-container .feedback', {duration: 1, autoAlpha: 1, onComplete: () => {this.canAnimateSlide = true}}, '-=1')

       this.timeline_1_11
        .set('.slide__1', {zIndex: 0})
        .set('.home-container .contacts', {zIndex: 21})
        .to('.slide .offer-sub', {duration: 1, x: -450, autoAlpha: 0}, '-=1')
        .to('.slide .offer-btn', {duration: 1, y: 250, autoAlpha: 0}, '-=1')
        .to('.slide .offer-title', {duration: 1, x: -250, autoAlpha: 0}, '-=1')
        .to('.slide .offer-text', {duration: 1, x: -55, autoAlpha: 0}, '-=1')
        .to('.home-container .car__tesla .car-services', { duration: 0.5, autoAlpha: 0, ease:'Expo.easeInOut'}, '-=1.5')
        .to('.home-container .offer-features .feature', {stagger: 0.2,duration: 1, y: 100, autoAlpha: 0}, '-=1')
        .to('.home-container .car__tesla', {duration: 2.5, xPercent: -250, ease:'Expo.easeInOut'}, '-=1.5')


        .to('.home-container .contacts', {duration: 1, autoAlpha: 1, onComplete: () => {this.canAnimateSlide = true}}, '-=1')

      //////// 1ST SLIDE ANIMATIONS
      //////// 2ST SLIDE ANIMATIONS

      this.timeline_2_1
        .set('.car__tesla', {zIndex: 23})

        .to('.animated__about-subtitle',{duration: 2, autoAlpha: 0, maxWidth: '0px', ease:'Expo.easeInOut'})
        .to('.animated__about-title',{duration: 2, autoAlpha: 0, maxWidth: '0px', ease:'Expo.easeInOut'}, '-=2')
        .to('.animated__about-text-1',{duration: 2, autoAlpha: 0, maxWidth: '0px', ease:'Expo.easeInOut'}, '-=2')
        .to('.animated__about-text-2',{duration: 2, autoAlpha: 0, maxWidth: '0px', ease:'Expo.easeInOut'}, '-=2')
        .to('.home-container .about-bg', {duration: 1, autoAlpha: 0}, '-=2')
        .to('.home-container .about-video', {duration: 1, autoAlpha: 0, y: 100}, '-=2')
        .to('.home-container .about-return',{duration: 1, autoAlpha: 0, x: 100}, '-=2')

        .to('.slide .offer-sub', {duration: 1, x: 0, autoAlpha: 1}, '-=1')
        .to('.slide .offer-btn', {duration: 1, y: 0, autoAlpha: 1}, '-=1')
        .to('.slide .offer-title', {duration: 1, x: 0, autoAlpha: 1}, '-=1')
        .to('.slide .offer-text', {duration: 1, x: 0, autoAlpha: 1}, '-=1')
        .to('.car__tesla .car-services', { duration: 0.5, autoAlpha: 1, ease:'Expo.easeInOut'}, '-=1')
        .to('.home-container .offer-features .feature', {stagger: 0.2,duration: 1, y: 0, autoAlpha: 1}, '-=1')
        .set('.home-container .slide__1', {zIndex: 22})
        .to('.home-container .car__tesla', {duration: 2.5, xPercent: -0, ease:'Expo.easeInOut', onComplete: () => {
          this.canAnimateSlide = true
        }}, '-=2.5')


      this.timeline_2_3
        .set('.car__tesla', {zIndex: 0})
        .set('.home-container .choose-btn', {zIndex: 22})
        // .to('.animated__about-subtitle', {duration: 1, autoAlpha: 0}, '-=1')
        // .to('.animated__about-title', {duration: 1, autoAlpha: 0}, '-=1')
        // .to('.animated__about-text-1', {duration: 1, autoAlpha: 0}, '-=1')
        // .to('.animated__about-text-2', {duration: 1, autoAlpha: 0}, '-=1')

        .to('.animated__about-subtitle',{duration: 2, autoAlpha: 0, maxWidth: '0px', ease:'Expo.easeInOut'}, '-=2')
        .to('.animated__about-title',{duration: 2, autoAlpha: 0, maxWidth: '0px', ease:'Expo.easeInOut'}, '-=2')
        .to('.animated__about-text-1',{duration: 2, autoAlpha: 0, maxWidth: '0px', ease:'Expo.easeInOut'}, '-=2')
        .to('.animated__about-text-2',{duration: 2, autoAlpha: 0, maxWidth: '0px', ease:'Expo.easeInOut'}, '-=2')
        .to('.home-container .about-bg', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .about-video', {duration: 1, autoAlpha: 0, y: 100}, '-=1')
        .fromTo('.home-container .choose-car',{scale: 0.8, autoAlpha: 0}, {duration: 1, autoAlpha: 1, scale: 1} )
        .fromTo('.home-container .choose-subtitle',{scale: 0.8, autoAlpha: 0}, {duration: 1, autoAlpha: 1, scale: 1}, '-=1' )
        .fromTo('.home-container .choose-text',{scale: 0.8, autoAlpha: 0}, {duration: 1, autoAlpha: 1, scale: 1}, '-=1' )
        .fromTo('.home-container .choose-btn',{y: 200, autoAlpha: 0}, {duration: 1, autoAlpha: 1, y: 0}, '-=1')
        .fromTo('.home-container .choose-values',{scale: 0.8, autoAlpha: 0}, {duration: 1, autoAlpha: 1, scale: 1, onComplete: () => {
          this.canAnimateSlide = true

        }, onReverseComplete: () => {
              this.canAnimateSlide = true
          }}, '-=1' )


       this.timeline_2_4 //From Choose 3 slide (About 2nd) To Services 4 slide(1st RestorFX)

        .set('.home-container .services-item__restorfx', {scale: 1.5, autoAlpha: 1})
        .to('.animated__about-subtitle',{duration: 2, autoAlpha: 0, maxWidth: '0px', ease:'Expo.easeInOut'})
        .to('.animated__about-title',{duration: 2, autoAlpha: 0, maxWidth: '0px', ease:'Expo.easeInOut'}, '-=2')
        .to('.animated__about-text-1',{duration: 2, autoAlpha: 0, maxWidth: '0px', ease:'Expo.easeInOut'}, '-=2')
        .to('.animated__about-text-2',{duration: 2, autoAlpha: 0, maxWidth: '0px', ease:'Expo.easeInOut'}, '-=2')
        .to('.home-container .about-return',{duration: 1, autoAlpha: 0, x: 100}, '-=2')
        .to('.home-container .about-bg', {duration: 1, autoAlpha: 0}, '-=2')
        .to('.home-container .about-video', {duration: 1, autoAlpha: 0, y: 100}, '-=2')
        .to('.home-container .car__tesla', {duration: 1.75, xPercent: -250, ease:'Expo.easeInOut'}, '-=1.5')

        .to('.home-container .services-left', {duration: 1, autoAlpha: 1}, '-=0.5')
        .to('.home-container .services-right', {duration: 1, autoAlpha: 1}, '-=1')
        .to('.home-container .services-car__restorfx', {duration: 1, autoAlpha: 1}, '-=1')
        .to('.home-container .services-text__restorfx', {duration: 1, autoAlpha: 1}, '-=1')
        .set('.home-container .services-features__restorfx', {duration: 1, autoAlpha: 1}, '-=1')
        .to('.home-container .services-features__restorfx .feature', {duration: 0.5, stagger: 0.1, autoAlpha: 1, y: -120, onComplete: () => {this.canAnimateSlide = true}}, '-=1')

       this.timeline_2_9
        .to('.animated__about-subtitle',{duration: 2, autoAlpha: 0, maxWidth: '0px', ease:'Expo.easeInOut'})
        .to('.animated__about-title',{duration: 2, autoAlpha: 0, maxWidth: '0px', ease:'Expo.easeInOut'}, '-=2')
        .to('.animated__about-text-1',{duration: 2, autoAlpha: 0, maxWidth: '0px', ease:'Expo.easeInOut'}, '-=2')
        .to('.animated__about-text-2',{duration: 2, autoAlpha: 0, maxWidth: '0px', ease:'Expo.easeInOut'}, '-=2')
        .to('.home-container .about-return',{duration: 1, autoAlpha: 0, x: 100}, '-=1')
        .to('.home-container .about-bg', {duration: 1, autoAlpha: 0}, '-=2')
        .to('.home-container .about-video', {duration: 1, autoAlpha: 0, y: 100}, '-=2')
        .to('.home-container .car__tesla', {duration: 1.75, xPercent: -250, ease:'Expo.easeInOut'}, '-=1.5')


        .to('.home-container .feedback', {duration: 1, autoAlpha: 1, onComplete: () => {this.canAnimateSlide = true}}, '-=0.5')

       this.timeline_2_11
        .to('.animated__about-subtitle',{duration: 2, autoAlpha: 0, maxWidth: '0px', ease:'Expo.easeInOut'})
        .to('.animated__about-title',{duration: 2, autoAlpha: 0, maxWidth: '0px', ease:'Expo.easeInOut'}, '-=2')
        .to('.animated__about-text-1',{duration: 2, autoAlpha: 0, maxWidth: '0px', ease:'Expo.easeInOut'}, '-=2')
        .to('.animated__about-text-2',{duration: 2, autoAlpha: 0, maxWidth: '0px', ease:'Expo.easeInOut'}, '-=2')
        .to('.home-container .about-return',{duration: 1, autoAlpha: 0, x: 100}, '-=1')
        .to('.home-container .about-bg', {duration: 1, autoAlpha: 0}, '-=2')
        .to('.home-container .about-video', {duration: 1, autoAlpha: 0, y: 100}, '-=2')
        .to('.home-container .car__tesla', {duration: 1.75, xPercent: -250, ease:'Expo.easeInOut'}, '-=1.5')


        .to('.home-container .contacts', {duration: 1, autoAlpha: 1, onComplete: () => {this.canAnimateSlide = true}}, '-=0.5')

      //////// 2ST SLIDE ANIMATIONS
      //////// 3ST SLIDE ANIMATIONS

      this.timeline_3_1
        .set('.home-container .offer', {zIndex: 22})
        .set('.home-container .car__tesla', {zIndex: 23})
        .to('.home-container .choose-car', {duration: 1, autoAlpha: 0, scale: 0.8} )
        .to('.home-container .choose-subtitle', {duration: 1, autoAlpha: 0, scale: 0.8}, '-=1' )
        .to('.home-container .choose-text', {duration: 1, autoAlpha: 0, scale: 0.8}, '-=1' )
        .to('.home-container .choose-btn', {duration: 1, autoAlpha: 0, y: 200}, '-=1')
        .to('.home-container .choose-values', {duration: 1, autoAlpha: 0, scale: 0.8}, '-=1')

        .to('.home-container .about-return',{duration: 1, autoAlpha: 0, x: 100}, '-=1')
        .to('.slide .offer-sub', {duration: 1, x: 0, autoAlpha: 1}, )
        .to('.slide .offer-btn', {duration: 1, y: 0, autoAlpha: 1}, '-=1')
        .to('.slide .offer-title', {duration: 1, x: 0, autoAlpha: 1}, '-=1')
        .to('.slide .offer-text', {duration: 1, x: 0, autoAlpha: 1}, '-=1')
        .to('.car__tesla .car-services', { duration: 0.5, autoAlpha: 1, ease:'Expo.easeInOut'}, '-=1.5')
        .to('.home-container .offer-features .feature', {stagger: 0.2,duration: 0.6, y: 0, autoAlpha: 1}, '-=1')
        .to('.home-container .car__tesla', {duration: 1.75, xPercent: 0, ease:'Expo.easeInOut', onComplete: () => {
          this.canAnimateSlide = true
        }, onReverseComplete: () => {
          this.canAnimateSlide = true
        }}, '-=1.5')

        this.timeline_3_2
        .set('.car__tesla', {zIndex: 0})
        .set('.home-container .choose-btn', {zIndex: 22})

        .to('.home-container .choose-car',{duration: 1, scale: 0.8, autoAlpha: 0} )
        .to('.home-container .choose-subtitle',{duration: 1, scale: 0.8, autoAlpha: 0}, '-=1' )
        .to('.home-container .choose-text',{duration: 1, scale: 0.8, autoAlpha: 0}, '-=1' )
        .to('.home-container .choose-btn',{y: 200, autoAlpha: 0}, '-=1')
        .to('.home-container .choose-values',{duration: 1, scale: 0.8, autoAlpha: 0}, '-=1' )
        .to('.animated__about-subtitle', {duration: 2, autoAlpha: 1, maxWidth: '220px', ease:'Expo.easeInOut'}, '-=1')
        .to('.animated__about-title', {duration: 2, autoAlpha: 1, maxWidth: '738px', ease:'Expo.easeInOut'}, '-=2')
        .to('.animated__about-text-1', {duration: 2, autoAlpha: 1, maxWidth: '383px', ease:'Expo.easeInOut'}, '-=2')
        .to('.animated__about-text-2', {duration: 2, autoAlpha: 1, maxWidth: '292px', ease:'Expo.easeInOut'}, '-=2')
        .to('.home-container .about-bg', {duration: 1.5, autoAlpha: 1}, '-=1')
        .to('.home-container .about-return',{duration: 1.5, autoAlpha: 1, x: 0}, '-=1.5')
        .fromTo('.home-container .about-video', {y: 100, autoAlpha: 0},{duration: 1, autoAlpha: 1, y: 0, onComplete: () => {
            this.canAnimateSlide = true
        }}, '-=1.25')

       this.timeline_3_4 //From Choose 3 slide (About 2nd) To Services 4 slide(1st RestorFX)
        .set('.home-container .services-item__restorfx', {scale: 1.5, autoAlpha: 1})
        .to('.home-container .choose-car', {duration: 1, autoAlpha: 0, scale: 0.8} )
        .to('.home-container .choose-subtitle', {duration: 1, autoAlpha: 0, scale: 0.8}, '-=1' )
        .to('.home-container .choose-text', {duration: 1, autoAlpha: 0, scale: 0.8}, '-=1' )
        .to('.home-container .choose-btn', {duration: 1, autoAlpha: 0, y: 200}, '-=1')
        .to('.home-container .choose-values', {duration: 1, autoAlpha: 0, scale: 0.8}, '-=1')
        .to('.home-container .about-return',{duration: 1, autoAlpha: 0, x: 100}, '-=1')
        .to('.home-container .car__tesla', {duration: 1.75, xPercent: -250, ease:'Expo.easeInOut'}, '-=0.5')

        .to('.home-container .services-left', {duration: 1, autoAlpha: 1}, '-=0.5')
        .to('.home-container .services-right', {duration: 1, autoAlpha: 1}, '-=1')
        .to('.home-container .services-car__restorfx', {duration: 1, autoAlpha: 1}, '-=1')
        .to('.home-container .services-text__restorfx', {duration: 1, autoAlpha: 1}, '-=1')
        // .to('.home-container .services-item__restorfx', {duration: 1, autoAlpha: 0.2}, '-=1')
        .set('.home-container .services-features__restorfx', {duration: 1, autoAlpha: 1}, '-=1')
        .to('.home-container .services-features__restorfx .feature', {duration: 0.5, stagger: 0.1, autoAlpha: 1, y: -120, onComplete: () => {this.canAnimateSlide = true}}, '-=1')
        // .to('.home-container .services-features__restorfx', {duration: 1, autoAlpha: 1, onComplete: () => {this.canAnimateSlide = true}}, '-=1')

      this.timeline_3_9

        .to('.home-container .choose-car', {duration: 1, autoAlpha: 0, scale: 0.8} )
        .to('.home-container .choose-subtitle', {duration: 1, autoAlpha: 0, scale: 0.8}, '-=1' )
        .to('.home-container .choose-text', {duration: 1, autoAlpha: 0, scale: 0.8}, '-=1' )
        .to('.home-container .choose-btn', {duration: 1, autoAlpha: 0, y: 200}, '-=1')
        .to('.home-container .choose-values', {duration: 1, autoAlpha: 0, scale: 0.8}, '-=1')
        .to('.home-container .about-return',{duration: 1, autoAlpha: 0, x: 100}, '-=1')
        .to('.home-container .car__tesla', {duration: 1.75, xPercent: -250, ease:'Expo.easeInOut'}, '-=0.5')

        .to('.home-container .feedback', {duration: 1, autoAlpha: 1, onComplete: () => {this.canAnimateSlide = true}}, '-=0.5')

      this.timeline_3_11
        .to('.home-container .choose-car', {duration: 1, autoAlpha: 0, scale: 0.8} )
        .to('.home-container .choose-subtitle', {duration: 1, autoAlpha: 0, scale: 0.8}, '-=1' )
        .to('.home-container .choose-text', {duration: 1, autoAlpha: 0, scale: 0.8}, '-=1' )
        .to('.home-container .choose-btn', {duration: 1, autoAlpha: 0, y: 200}, '-=1')
        .to('.home-container .choose-values', {duration: 1, autoAlpha: 0, scale: 0.8}, '-=1')
        .to('.home-container .about-return',{duration: 1, autoAlpha: 0, x: 100}, '-=1')
        .to('.home-container .car__tesla', {duration: 1.75, xPercent: -250, ease:'Expo.easeInOut'}, '-=0.5')

        .to('.home-container .contacts', {duration: 1, autoAlpha: 1, onComplete: () => {this.canAnimateSlide = true}}, '-=0.5')

      //////// 3ST SLIDE ANIMATIONS
      //////// 4ST SLIDE ANIMATIONS
      ///
      this.timeline_4_1
        .set('.slide__4', {zIndex: 0})

        .to('.home-container .services-left', {duration: 1, autoAlpha: 0})
        .to('.home-container .services-right', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-car__restorfx', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-text__restorfx', {duration: 1, autoAlpha: 0}, '-=1')
        // .set('.home-container .services-features__restorfx', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-features__restorfx .feature', {duration: 0.5, stagger: 0.1, autoAlpha: 0, y: 0}, '-=1')


        .to('.slide .offer-sub', {duration: 1, x: 0, autoAlpha: 1})
        .to('.slide .offer-btn', {duration: 1, y: 0, autoAlpha: 1}, '-=1')
        .to('.slide .offer-title', {duration: 1, x: 0, autoAlpha: 1}, '-=1')
        .to('.slide .offer-text', {duration: 1, x: 0, autoAlpha: 1}, '-=1')
        .to('.car__tesla .car-services', { duration: 0.5, autoAlpha: 1, ease:'Expo.easeInOut'}, '-=1')
        .to('.home-container .offer-features .feature', {stagger: 0.2,duration: 1, y: 0, autoAlpha: 1}, '-=1')
        .set('.home-container .slide__1', {zIndex: 22})
        .to('.home-container .car__tesla', {duration: 2.5, xPercent: -0, ease:'Expo.easeInOut', onComplete: () => {
          this.canAnimateSlide = true
        }}, '-=2.5')


      this.timeline_4_2
        .set('.home-container .slide__2', {zIndex: 22, autoAlpha: 1})
        .set('.slide__4', {zIndex: 0})

        .to('.home-container .services-left', {duration: 1, autoAlpha: 0})
        .to('.home-container .services-right', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-car__restorfx', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-text__restorfx', {duration: 1, autoAlpha: 0}, '-=1')
        .set('.home-container .services-features__restorfx', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-features__restorfx .feature', {duration: 0.5, stagger: 0.1, autoAlpha: 0, y: 0, onComplete: () => {this.canAnimateSlide = true}}, '-=1')

        .to('.home-container .car__tesla .car-services', { duration: 0.5, autoAlpha: 0, ease:'Expo.easeInOut'})
        .to('.home-container .offer-features .feature', {stagger: 0.2,duration: 1, y: 100, autoAlpha: 0}, '-=1.5')
        .to('.home-container .car__tesla', {duration: 1.75, xPercent: -136, ease:'Expo.easeInOut'}, '-=1.5')
        .to('.animated__about-subtitle', {duration: 2, autoAlpha: 1, maxWidth: '220px', ease:'Expo.easeInOut'}, '-=1')
        .to('.animated__about-title', {duration: 2, autoAlpha: 1, maxWidth: '738px', ease:'Expo.easeInOut'}, '-=2')
        .to('.animated__about-text-1', {duration: 2, autoAlpha: 1, maxWidth: '383px', ease:'Expo.easeInOut'}, '-=2')
        .to('.animated__about-text-2', {duration: 2, autoAlpha: 1, maxWidth: '292px', ease:'Expo.easeInOut'}, '-=2')
        .to('.home-container .about-bg', {duration: 1.5, autoAlpha: 1}, '-=2')
        .fromTo('.home-container .about-return', {x: 100, autoAlpha: 0},{duration: 1.5, autoAlpha: 1, x: 0}, '-=1.5')
        .fromTo('.home-container .about-video', {y: 100, autoAlpha: 0},{duration: 1, autoAlpha: 1, y: 0, onComplete: () => {
            this.canAnimateSlide = true
        }}, '-=1.25')


      this.timeline_4_3
        .set('.car__tesla', {zIndex: 0})
        .set('.slide__4', {zIndex: 0})
        .set('.home-container .choose-btn', {zIndex: 22})

        .to('.home-container .services-left', {duration: 1, autoAlpha: 0})
        .to('.home-container .services-right', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-car__restorfx', {duration: 1, autoAlpha: 0}, '-=1')
        .set('.home-container .services-features__restorfx', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-features__restorfx .feature', {duration: 0.5, stagger: 0.1, autoAlpha: 0, y: 0}, '-=1')

        .to('.home-container .offer-features .feature', {stagger: 0.2,duration: 1, y: 100, autoAlpha: 0}, '-=1')
        .to('.home-container .car__tesla', {duration: 3.75, xPercent: -136, ease:'Expo.easeInOut'}, '-=2')

        .to('.home-container .about-bg', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .about-return',{duration: 1, autoAlpha: 1, x: 0}, '-=1')
        .to('.home-container .about-video', {duration: 1, autoAlpha: 0, y: 100}, '-=1')
        .fromTo('.home-container .choose-car',{scale: 0.8, autoAlpha: 0}, {duration: 1, autoAlpha: 1, scale: 1}, '-=1.2' )
        .fromTo('.home-container .choose-subtitle',{scale: 0.8, autoAlpha: 0}, {duration: 1, autoAlpha: 1, scale: 1}, '-=1.2' )
        .fromTo('.home-container .choose-text',{scale: 0.8, autoAlpha: 0}, {duration: 1, autoAlpha: 1, scale: 1}, '-=1.2' )
        .fromTo('.home-container .choose-btn',{y: 200, autoAlpha: 0}, {duration: 1, autoAlpha: 1, y: 0}, '-=1.2')
        .fromTo('.home-container .choose-values',{scale: 0.8, autoAlpha: 0}, {duration: 1, autoAlpha: 1, scale: 1, onComplete: () => {
          this.canAnimateSlide = true
        }}, '-=1.2' )




      this.timeline_4_5 //RestorFX to ClearFX (4 to 5)
        .to('.home-container .services-items-wrapper', {duration: 1, y: 0}, '-=1')
        .to('.home-container .services-car__restorfx', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-text__restorfx', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-item__restorfx', {duration: 0.5, scale: 1, opacity: 0.2}, '-=1')
        .set('.home-container .services-features__restorfx', {duration: 1, autoAlpha: 1}, '-=0.5')
        .to('.home-container .services-features__restorfx .feature', {duration: 0.5, stagger: 0.1, autoAlpha: 0, y: 0}, '-=1')

        .to('.home-container .services-car__clearfx', {duration: 1, autoAlpha: 1}, '-=1')

        .to('.home-container .services-text__clearfx', {duration: 1, autoAlpha: 1}, '-=1')
        .to('.home-container .services-item__clearfx', {duration: 0.5, autoAlpha: 1, opacity: 1, scale: 1.5}, '-=1')
        .to('.home-container .services-features__clearfx .feature', {duration: 0.5, stagger: 0.1, autoAlpha: 1, y: -120, onComplete: () => {this.canAnimateSlide = true}}, '-=0.5')

      this.timeline_4_9

        .set('.slide__4', {zIndex: 0})
        .to('.home-container .services-left', {duration: 1, autoAlpha: 0})
        .to('.home-container .services-right', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-car__restorfx', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-text__restorfx', {duration: 1, autoAlpha: 0}, '-=1')

        .set('.home-container .services-features__restorfx', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-features__restorfx .feature', {duration: 0.5, stagger: 0.1, autoAlpha: 0, y: 0}, '-=1')


        .to('.home-container .feedback', {duration: 1, autoAlpha: 1, onComplete: () => {this.canAnimateSlide = true}})


      this.timeline_4_11

        .set('.slide__4', {zIndex: 0})
        .to('.home-container .services-left', {duration: 1, autoAlpha: 0})
        .to('.home-container .services-right', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-car__restorfx', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-text__restorfx', {duration: 1, autoAlpha: 0}, '-=1')
        // .to('.home-container .services-item__restorfx', {duration: 1, autoAlpha: 0.2}, '-=1')
        .set('.home-container .services-features__restorfx', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-features__restorfx .feature', {duration: 0.5, stagger: 0.1, autoAlpha: 0, y: 0}, '-=1')

        .to('.home-container .contacts', {duration: 1, autoAlpha: 1, onComplete: () => {this.canAnimateSlide = true}})




      //////// 4ST SLIDE ANIMATIONS
      //////// 5ST SLIDE ANIMATIONS
      ///
      this.timeline_5_1
        .to('.home-container .services-left', {duration: 1, autoAlpha: 0})
        .to('.home-container .services-right', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-car__clearfx', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-text__clearfx', {duration: 1, autoAlpha: 0}, '-=1')
        // .set('.home-container .services-features__clearfx', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-features__clearfx .feature', {duration: 0.5, stagger: 0.1, autoAlpha: 0, y: 0}, '-=1')


        .to('.slide .offer-sub', {duration: 1, x: 0, autoAlpha: 1})
        .to('.slide .offer-btn', {duration: 1, y: 0, autoAlpha: 1}, '-=1')
        .to('.slide .offer-title', {duration: 1, x: 0, autoAlpha: 1}, '-=1')
        .to('.slide .offer-text', {duration: 1, x: 0, autoAlpha: 1}, '-=1')
        .to('.car__tesla .car-services', { duration: 0.5, autoAlpha: 1, ease:'Expo.easeInOut'}, '-=1')
        .to('.home-container .offer-features .feature', {stagger: 0.2,duration: 1, y: 0, autoAlpha: 1}, '-=1')
        .set('.home-container .slide__1', {zIndex: 22})

        .set('.home-container .services-items-wrapper', {y: 70})
        .set('.home-container .services-item__clearfx', {opacity: 0.2, scale: 1})
        .set('.home-container .services-item__restorfx', {scale: 1.5, autoAlpha: 1})
        .to('.home-container .car__tesla', {duration: 2.5, xPercent: -0, ease:'Expo.easeInOut', onComplete: () => {
          this.canAnimateSlide = true
        }}, '-=2.5')

        this.timeline_5_2
          .set('.home-container .slide__2', {zIndex: 22, autoAlpha: 1})
          .to('.home-container .services-left', {duration: 1, autoAlpha: 0})
          .to('.home-container .services-right', {duration: 1, autoAlpha: 0}, '-=1')

          // .set('.home-container .services-features__clearfx', {duration: 1, autoAlpha: 0}, '-=1')
          .to('.home-container .services-car__clearfx', {duration: 1, autoAlpha: 0}, '-=1')
          .to('.home-container .services-text__clearfx', {duration: 1, autoAlpha: 0}, '-=1')
          .to('.home-container .services-features__clearfx .feature', {duration: 0.5, stagger: 0.1, autoAlpha: 0, y: 0}, '-=1')


          .to('.home-container .car__tesla .car-services', { duration: 0.5, autoAlpha: 0, ease:'Expo.easeInOut'})
          .to('.home-container .offer-features .feature', {stagger: 0.2,duration: 1, y: 100, autoAlpha: 0}, '-=1.5')
          .to('.home-container .car__tesla', {duration: 1.75, xPercent: -136, ease:'Expo.easeInOut'}, '-=1.5')

          .to('.animated__about-subtitle', {duration: 2, autoAlpha: 1, maxWidth: '220px', ease:'Expo.easeInOut'}, '-=1')
          .to('.animated__about-title', {duration: 2, autoAlpha: 1, maxWidth: '738px', ease:'Expo.easeInOut'}, '-=2')
          .to('.animated__about-text-1', {duration: 2, autoAlpha: 1, maxWidth: '383px', ease:'Expo.easeInOut'}, '-=2')
          .to('.animated__about-text-2', {duration: 2, autoAlpha: 1, maxWidth: '292px', ease:'Expo.easeInOut'}, '-=2')
          .to('.home-container .about-bg', {duration: 1.5, autoAlpha: 1}, '-=2')

          .set('.home-container .services-items-wrapper', {y: 70})
          .set('.home-container .services-item__clearfx', {opacity: 0.2, scale: 1})
          .set('.home-container .services-item__restorfx', {scale: 1.5, autoAlpha: 1})
          .fromTo('.home-container .about-return', {x: 100, autoAlpha: 0},{duration: 1.5, autoAlpha: 1, x: 0}, '-=1.5')
          .fromTo('.home-container .about-video', {y: 100, autoAlpha: 0},{duration: 1, autoAlpha: 1, y: 0, onComplete: () => {
              this.canAnimateSlide = true
          }}, '-=1.25')

      this.timeline_5_4
        .to('.home-container .services-items-wrapper', {duration: 1, y: 70})

        .to('.home-container .services-car__clearfx', {duration: 1, autoAlpha: 0}, '-=1')

        .to('.home-container .services-text__clearfx', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-item__clearfx', {duration: 0.5, opacity: 0.2, scale: 1}, '-=1')
        // .set('.home-container .services-features__clearfx', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-features__clearfx .feature', {duration: 0.5, stagger: 0.1, autoAlpha: 0, y: 0}, '-=1')

        .to('.home-container .services-item__restorfx', {scale: 1.5, autoAlpha: 1}, '-=1')
        .to('.home-container .services-text__restorfx', {duration: 1, autoAlpha: 1}, '-=1')
        .to('.home-container .services-car__restorfx', {duration: 1, autoAlpha: 1}, '-=1')
        // .set('.home-container .services-features__restorfx', {duration: 1, autoAlpha: 1}, '-=1')
        .to('.home-container .services-features__restorfx .feature', {duration: 0.5, stagger: 0.1, autoAlpha: 1, y: -120, onComplete: () => {this.canAnimateSlide = true}}, '-=1')


      this.timeline_5_6 //Clearfx to PDR (5 to 6)
        .to('.home-container .services-items-wrapper', {duration: 1, y: -75}, '-=1')
        .to('.home-container .services-car__clearfx', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-text__clearfx', {duration: 1, autoAlpha: 0}, '-=1')

        .to('.home-container .services-item__clearfx', {duration: 0.5, opacity: 0.2, scale: 1}, '-=1')
        .to('.home-container .services-features__clearfx .feature', {duration: 0.5, stagger: 0.1, autoAlpha: 0, y: 0}, '-=1')

        .to('.home-container .services-car__pdr', {duration: 1, autoAlpha: 1}, '-=1')
        .to('.home-container .services-text__pdr', {duration: 1, autoAlpha: 1}, '-=1')
        .to('.home-container .services-item__pdr', {duration: 0.5, opacity: 1, scale: 1.5}, '-=1')
        .to('.home-container .services-features__pdr .feature', {duration: 0.5, stagger: 0.1, autoAlpha: 1, y: -120, onComplete: () => {this.canAnimateSlide = true}}, '-=0.5')


       this.timeline_5_9

        .to('.home-container .services-left', {duration: 1, autoAlpha: 0})
        .to('.home-container .services-right', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-car__clearfx', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-text__clearfx', {duration: 1, autoAlpha: 0}, '-=1')
        // .set('.home-container .services-features__clearfx', {duration: 1, autoAlpha: 0}, '-=0.5')
        .to('.home-container .services-features__clearfx .feature', {duration: 0.5, stagger: 0.1, autoAlpha: 0, y: 0}, '-=1')


        .set('.home-container .services-items-wrapper', {y: 70})
        .set('.home-container .services-item__clearfx', {opacity: 0.2, scale: 1})
        .set('.home-container .services-item__restorfx', {scale: 1.5, autoAlpha: 1})

        .to('.home-container .feedback', {duration: 1, autoAlpha: 1, onComplete: () => {this.canAnimateSlide = true}})



       this.timeline_5_11

        .to('.home-container .services-left', {duration: 1, autoAlpha: 0})
        .to('.home-container .services-right', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-car__clearfx', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-text__clearfx', {duration: 1, autoAlpha: 0}, '-=1')
        .set('.home-container .services-features__clearfx', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-features__clearfx .feature', {duration: 0.5, stagger: 0.1, autoAlpha: 0, y: 0}, '-=1')
        .set('.home-container .services-items-wrapper', {y: 70})
        .set('.home-container .services-item__clearfx', {opacity: 0.2, scale: 1})
        .set('.home-container .services-item__restorfx', {scale: 1.5, autoAlpha: 1})

        .to('.home-container .contacts', {duration: 1, autoAlpha: 1, onComplete: () => {this.canAnimateSlide = true}})


      //////// 5ST SLIDE ANIMATIONS
      //////// 6ST SLIDE ANIMATIONS
      ///
      ///
      this.timeline_6_1
        .set('.slide__4', {zIndex: 0})

        .to('.home-container .services-left', {duration: 1, autoAlpha: 0})
        .to('.home-container .services-right', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-car__pdr', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-text__pdr', {duration: 1, autoAlpha: 0}, '-=1')
        // .set('.home-container .services-features__pdr', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-features__pdr .feature', {duration: 0.5, stagger: 0.1, autoAlpha: 0, y: 0}, '-=1')


        .to('.slide .offer-sub', {duration: 1, x: 0, autoAlpha: 1})
        .to('.slide .offer-btn', {duration: 1, y: 0, autoAlpha: 1}, '-=1')
        .to('.slide .offer-title', {duration: 1, x: 0, autoAlpha: 1}, '-=1')
        .to('.slide .offer-text', {duration: 1, x: 0, autoAlpha: 1}, '-=1')
        .to('.car__tesla .car-services', { duration: 0.5, autoAlpha: 1, ease:'Expo.easeInOut'}, '-=1')
        .to('.home-container .offer-features .feature', {stagger: 0.2,duration: 1, y: 0, autoAlpha: 1}, '-=1')
        .set('.home-container .slide__1', {zIndex: 22})

          .set('.home-container .services-items-wrapper', {y: 70})
          .set('.home-container .services-item__pdr', {opacity: 0.2, scale: 1})
          .set('.home-container .services-item__restorfx', {scale: 1.5, autoAlpha: 1})
        .to('.home-container .car__tesla', {duration: 2.5, xPercent: -0, ease:'Expo.easeInOut', onComplete: () => {
          this.canAnimateSlide = true
        }}, '-=2.5')

        this.timeline_6_2
          .set('.home-container .slide__2', {zIndex: 22, autoAlpha: 1})
          .to('.home-container .services-left', {duration: 1, autoAlpha: 0})
          .to('.home-container .services-right', {duration: 1, autoAlpha: 0}, '-=1')

          // .set('.home-container .services-features__pdr', {duration: 1, autoAlpha: 0}, '-=1')
          .to('.home-container .services-car__pdr', {duration: 1, autoAlpha: 0}, '-=1')
          .to('.home-container .services-text__pdr', {duration: 1, autoAlpha: 0}, '-=1')
          .to('.home-container .services-features__pdr .feature', {duration: 0.5, stagger: 0.1, autoAlpha: 0, y: 0}, '-=1')


          .to('.home-container .car__tesla .car-services', { duration: 0.5, autoAlpha: 0, ease:'Expo.easeInOut'})
          .to('.home-container .offer-features .feature', {stagger: 0.2,duration: 1, y: 100, autoAlpha: 0}, '-=1.5')
          .to('.home-container .car__tesla', {duration: 1.75, xPercent: -136, ease:'Expo.easeInOut'}, '-=1.5')

          .to('.animated__about-subtitle', {duration: 2, autoAlpha: 1, maxWidth: '220px', ease:'Expo.easeInOut'}, '-=1')
          .to('.animated__about-title', {duration: 2, autoAlpha: 1, maxWidth: '738px', ease:'Expo.easeInOut'}, '-=2')
          .to('.animated__about-text-1', {duration: 2, autoAlpha: 1, maxWidth: '383px', ease:'Expo.easeInOut'}, '-=2')
          .to('.animated__about-text-2', {duration: 2, autoAlpha: 1, maxWidth: '292px', ease:'Expo.easeInOut'}, '-=2')
          .to('.home-container .about-bg', {duration: 1.5, autoAlpha: 1}, '-=2')

          .set('.home-container .services-items-wrapper', {y: 70})
          .set('.home-container .services-item__pdr', {opacity: 0.2, scale: 1})
          .set('.home-container .services-item__restorfx', {scale: 1.5, autoAlpha: 1})
          .fromTo('.home-container .about-return', {x: 100, autoAlpha: 0},{duration: 1.5, autoAlpha: 1, x: 0}, '-=1.5')
          .fromTo('.home-container .about-video', {y: 100, autoAlpha: 0},{duration: 1, autoAlpha: 1, y: 0, onComplete: () => {
              this.canAnimateSlide = true
          }}, '-=1.25')

      this.timeline_6_4
        .to('.home-container .services-items-wrapper', {duration: 1, y: 70})

        .to('.home-container .services-car__pdr', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-text__pdr', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-item__pdr', {duration: 0.5, opacity: 0.2, scale: 1}, '-=1')
        // .set('.home-container .services-features__pdr', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-features__pdr .feature', {duration: 0.5, stagger: 0.1, autoAlpha: 0, y: 0}, '-=1')

        .to('.home-container .services-item__restorfx', {scale: 1.5, autoAlpha: 1}, '-=1')
        .to('.home-container .services-car__restorfx', {duration: 1, autoAlpha: 1}, '-=1')
        // .set('.home-container .services-features__restorfx', {duration: 1, autoAlpha: 1}, '-=1')
        .to('.home-container .services-features__restorfx .feature', {duration: 0.5, stagger: 0.1, autoAlpha: 1, y: -120, onComplete: () => {this.canAnimateSlide = true}}, '-=1')


      this.timeline_6_5
        .to('.home-container .services-items-wrapper', {duration: 1, y: 0})

        .to('.home-container .services-car__pdr', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-text__pdr', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-item__pdr', {duration: 0.5, opacity: 0.2, scale: 1}, '-=1')
        // .set('.home-container .services-features__pdr', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-features__pdr .feature', {duration: 0.5, stagger: 0.1, autoAlpha: 0, y: 0}, '-=1')

        .to('.home-container .services-item__clearfx', {scale: 1.5, autoAlpha: 1}, '-=1')
        .to('.home-container .services-car__clearfx', {duration: 1, autoAlpha: 1}, '-=1')
        .to('.home-container .services-text__clearfx', {duration: 1, autoAlpha: 1}, '-=1')
        // .set('.home-container .services-features__clearfx', {duration: 1, autoAlpha: 1}, '-=1')
        .to('.home-container .services-features__clearfx .feature', {duration: 0.5, stagger: 0.1, autoAlpha: 1, y: -120, onComplete: () => {this.canAnimateSlide = true}}, '-=1')


      this.timeline_6_7 //Clearfx to PDR (5 to 6)
        .to('.home-container .services-items-wrapper', {duration: 1, y: -150}, '-=1')
        .to('.home-container .services-car__pdr', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-text__pdr', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-item__pdr', {duration: 0.5, opacity: 0.2, scale: 1}, '-=1')
        .to('.home-container .services-features__pdr .feature', {duration: 0.5, stagger: 0.1, autoAlpha: 0, y: 0}, '-=1')

        .to('.home-container .services-car__ppf', {duration: 1, autoAlpha: 1}, '-=1')
        .to('.home-container .services-text__ppf', {duration: 1, autoAlpha: 1}, '-=1')
        .to('.home-container .services-item__ppf', {duration: 0.5, opacity: 1, scale: 1.5}, '-=1')
        .to('.home-container .services-features__ppf .feature', {duration: 0.5, stagger: 0.1, autoAlpha: 1, y: -120, onComplete: () => {this.canAnimateSlide = true}}, '-=0.5')


       this.timeline_6_9

        .to('.home-container .services-left', {duration: 1, autoAlpha: 0})
        .to('.home-container .services-right', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-car__pdr', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-text__pdr', {duration: 1, autoAlpha: 0}, '-=1')
        // .set('.home-container .services-features__pdr', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-features__pdr .feature', {duration: 0.5, stagger: 0.1, autoAlpha: 0, y: 0}, '-=1')


        .set('.home-container .services-items-wrapper', {y: 70})
        .set('.home-container .services-item__pdr', {opacity: 0.2, scale: 1})
        .set('.home-container .services-item__restorfx', {scale: 1.5, autoAlpha: 1})
        .to('.home-container .feedback', {duration: 1, autoAlpha: 1, onComplete: () => {this.canAnimateSlide = true}})



       this.timeline_6_11

        .to('.home-container .services-left', {duration: 1, autoAlpha: 0})
        .to('.home-container .services-right', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-car__pdr', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-text__pdr', {duration: 1, autoAlpha: 0}, '-=1')
        // .set('.home-container .services-features__pdr', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-features__pdr .feature', {duration: 0.5, stagger: 0.1, autoAlpha: 0, y: 0}, '-=1')

        .set('.home-container .services-items-wrapper', {y: 70})
        .set('.home-container .services-item__pdr', {opacity: 0.2, scale: 1})
        .set('.home-container .services-item__restorfx', {scale: 1.5, autoAlpha: 1})
        .to('.home-container .contacts', {duration: 1, autoAlpha: 1, onComplete: () => {this.canAnimateSlide = true}})


      //SLIDe6 //////
      //SLIDe7 //////
      //
      ///
      this.timeline_7_1
        .set('.slide__4', {zIndex: 0})

        .to('.home-container .services-left', {duration: 1, autoAlpha: 0})
        .to('.home-container .services-right', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-car__ppf', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-text__ppf', {duration: 1, autoAlpha: 0}, '-=1')
        // .set('.home-container .services-features__ppf', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-features__ppf .feature', {duration: 0.5, stagger: 0.1, autoAlpha: 0, y: 0}, '-=1')


        .to('.slide .offer-sub', {duration: 1, x: 0, autoAlpha: 1})
        .to('.slide .offer-btn', {duration: 1, y: 0, autoAlpha: 1}, '-=1')
        .to('.slide .offer-title', {duration: 1, x: 0, autoAlpha: 1}, '-=1')
        .to('.slide .offer-text', {duration: 1, x: 0, autoAlpha: 1}, '-=1')
        .to('.car__tesla .car-services', { duration: 0.5, autoAlpha: 1, ease:'Expo.easeInOut'}, '-=1')
        .to('.home-container .offer-features .feature', {stagger: 0.2,duration: 1, y: 0, autoAlpha: 1}, '-=1')
        .set('.home-container .slide__1', {zIndex: 22})

          .set('.home-container .services-items-wrapper', {y: 70})
          .set('.home-container .services-item__ppf', {opacity: 0.2, scale: 1})
          .set('.home-container .services-item__restorfx', {scale: 1.5, autoAlpha: 1})
        .to('.home-container .car__tesla', {duration: 2.5, xPercent: -0, ease:'Expo.easeInOut', onComplete: () => {
          this.canAnimateSlide = true
        }}, '-=2.5')

       this.timeline_7_2
          .set('.home-container .slide__2', {zIndex: 22, autoAlpha: 1})
          .to('.home-container .services-left', {duration: 1, autoAlpha: 0})
          .to('.home-container .services-right', {duration: 1, autoAlpha: 0}, '-=1')

          .to('.home-container .services-car__ppf', {duration: 1, autoAlpha: 0}, '-=1')
          .to('.home-container .services-text__ppf', {duration: 1, autoAlpha: 0}, '-=1')
          .to('.home-container .services-features__ppf .feature', {duration: 0.5, stagger: 0.1, autoAlpha: 0, y: 0}, '-=1')


          .to('.home-container .car__tesla .car-services', { duration: 0.5, autoAlpha: 0, ease:'Expo.easeInOut'})
          .to('.home-container .offer-features .feature', {stagger: 0.2,duration: 1, y: 100, autoAlpha: 0}, '-=1.5')
          .to('.home-container .car__tesla', {duration: 1.75, xPercent: -136, ease:'Expo.easeInOut'}, '-=1.5')

          .to('.animated__about-subtitle', {duration: 2, autoAlpha: 1, maxWidth: '220px', ease:'Expo.easeInOut'}, '-=1')
          .to('.animated__about-title', {duration: 2, autoAlpha: 1, maxWidth: '738px', ease:'Expo.easeInOut'}, '-=2')
          .to('.animated__about-text-1', {duration: 2, autoAlpha: 1, maxWidth: '383px', ease:'Expo.easeInOut'}, '-=2')
          .to('.animated__about-text-2', {duration: 2, autoAlpha: 1, maxWidth: '292px', ease:'Expo.easeInOut'}, '-=2')
          .to('.home-container .about-bg', {duration: 1.5, autoAlpha: 1}, '-=2')

          .set('.home-container .services-items-wrapper', {y: 70})
          .set('.home-container .services-item__ppf', {opacity: 0.2, scale: 1})
          .set('.home-container .services-item__restorfx', {scale: 1.5, autoAlpha: 1})
          .fromTo('.home-container .about-return', {x: 100, autoAlpha: 0},{duration: 1.5, autoAlpha: 1, x: 0}, '-=1.5')
          .fromTo('.home-container .about-video', {y: 100, autoAlpha: 0},{duration: 1, autoAlpha: 1, y: 0, onComplete: () => {
              this.canAnimateSlide = true
          }}, '-=1.25')

      this.timeline_7_4
        .to('.home-container .services-items-wrapper', {duration: 1, y: 70})

        .to('.home-container .services-car__ppf', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-text__ppf', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-item__ppf', {duration: 0.5, opacity: 0.2, scale: 1}, '-=1')
        // .set('.home-container .services-features__ppf', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-features__ppf .feature', {duration: 0.5, stagger: 0.1, autoAlpha: 0, y: 0}, '-=1')

        .to('.home-container .services-item__restorfx', {scale: 1.5, autoAlpha: 1}, '-=1')
        .to('.home-container .services-car__restorfx', {duration: 1, autoAlpha: 1}, '-=1')
        .to('.home-container .services-text__restorfx', {duration: 1, autoAlpha: 1}, '-=1')
        // .set('.home-container .services-features__restorfx', {duration: 1, autoAlpha: 1}, '-=1')
        .to('.home-container .services-features__restorfx .feature', {duration: 0.5, stagger: 0.1, autoAlpha: 1, y: -120, onComplete: () => {this.canAnimateSlide = true}}, '-=1')

      this.timeline_7_6
        .to('.home-container .services-items-wrapper', {duration: 1, y: -75}, '-=1')
        .to('.home-container .services-car__ppf', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-text__ppf', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-item__ppf', {duration: 0.5, opacity: 0.2, scale: 1}, '-=1')
        .to('.home-container .services-features__ppf .feature', {duration: 0.5, stagger: 0.1, autoAlpha: 0, y: 0}, '-=1')


        .to('.home-container .services-car__pdr', {duration: 1, autoAlpha: 1}, '-=1')
        .to('.home-container .services-text__pdr', {duration: 1, autoAlpha: 1}, '-=1')
        .to('.home-container .services-item__pdr', {duration: 0.5, opacity: 1, scale: 1.5}, '-=1')
        .to('.home-container .services-features__pdr', {duration: 1, autoAlpha: 1}, '-=0.5')
        .to('.home-container .services-features__pdr .feature', {duration: 0.5, stagger: 0.1, autoAlpha: 1, y: -120, onComplete: () => {this.canAnimateSlide = true}}, '-=1')


      this.timeline_7_8 //PPF TO Dynoflex (7 to 8)
          .to('.home-container .services-items-wrapper', {duration: 1, y: -225}, '-=1')
          .to('.home-container .services-car__ppf', {duration: 1, autoAlpha: 0}, '-=1')
          .to('.home-container .services-text__ppf', {duration: 1, autoAlpha: 0}, '-=1')
          .to('.home-container .services-item__ppf', {duration: 0.5, opacity: 0.2, scale: 1}, '-=1')
          .to('.home-container .services-features__ppf .feature', {duration: 0.5, stagger: 0.1, autoAlpha: 0, y: 0}, '-=1')

        .to('.home-container .services-car__dynoflex', {duration: 1, autoAlpha: 1}, '-=1')
        .to('.home-container .services-text__dynoflex', {duration: 1, autoAlpha: 1}, '-=1')
        .to('.home-container .services-item__dynoflex', {duration: 0.5, opacity: 1, scale: 1.5}, '-=1')
        .to('.home-container .services-features__dynoflex .feature', {duration: 0.5, stagger: 0.1, autoAlpha: 1, y: -120, onComplete: () => {this.canAnimateSlide = true}}, '-=0.5')


     this.timeline_7_9

        .to('.home-container .services-left', {duration: 1, autoAlpha: 0})
        .to('.home-container .services-right', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-car__ppf', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-text__ppf', {duration: 1, autoAlpha: 0}, '-=1')
        .set('.home-container .services-features__ppf', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-features__ppf .feature', {duration: 0.5, stagger: 0.1, autoAlpha: 0, y: 0}, '-=1')

        .set('.home-container .services-items-wrapper', {y: 70})
        .set('.home-container .services-item__ppf', {opacity: 0.2, scale: 1})
        .set('.home-container .services-item__restorfx', {scale: 1.5, autoAlpha: 1})
        .to('.home-container .feedback', {duration: 1, autoAlpha: 1, onComplete: () => {this.canAnimateSlide = true}})



      this.timeline_7_11

        .to('.home-container .services-left', {duration: 1, autoAlpha: 0})
        .to('.home-container .services-right', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-car__ppf', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-text__ppf', {duration: 1, autoAlpha: 0}, '-=1')
        .set('.home-container .services-features__ppf', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-features__ppf .feature', {duration: 0.5, stagger: 0.1, autoAlpha: 0, y: 0}, '-=1')
        .set('.home-container .services-items-wrapper', {y: 70})
        .set('.home-container .services-item__ppf', {opacity: 0.2, scale: 1})
        .set('.home-container .services-item__restorfx', {scale: 1.5, autoAlpha: 1})

        .to('.home-container .contacts', {duration: 1, autoAlpha: 1, onComplete: () => {this.canAnimateSlide = true}})




        //SLIDe7 //////
        //SLIDe8 //////
        //
      ///
      this.timeline_8_1
        .set('.slide__4', {zIndex: 0})

        .to('.home-container .services-left', {duration: 1, autoAlpha: 0})
        .to('.home-container .services-right', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-car__dynoflex', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-text__dynoflex', {duration: 1, autoAlpha: 0}, '-=1')
        // .set('.home-container .services-features__dynoflex', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-features__dynoflex .feature', {duration: 0.5, stagger: 0.1, autoAlpha: 0, y: 0}, '-=1')


        .to('.slide .offer-sub', {duration: 1, x: 0, autoAlpha: 1})
        .to('.slide .offer-btn', {duration: 1, y: 0, autoAlpha: 1}, '-=1')
        .to('.slide .offer-title', {duration: 1, x: 0, autoAlpha: 1}, '-=1')
        .to('.slide .offer-text', {duration: 1, x: 0, autoAlpha: 1}, '-=1')
        .to('.car__tesla .car-services', { duration: 0.5, autoAlpha: 1, ease:'Expo.easeInOut'}, '-=1')
        .to('.home-container .offer-features .feature', {stagger: 0.2,duration: 1, y: 0, autoAlpha: 1}, '-=1')
        .set('.home-container .slide__1', {zIndex: 22})

          .set('.home-container .services-items-wrapper', {y: 70})
          .set('.home-container .services-item__dynoflex', {opacity: 0.2, scale: 1})
          .set('.home-container .services-item__restorfx', {scale: 1.5, autoAlpha: 1})
        .to('.home-container .car__tesla', {duration: 2.5, xPercent: -0, ease:'Expo.easeInOut', onComplete: () => {
          this.canAnimateSlide = true
        }}, '-=2.5')

      this.timeline_8_2
        .set('.home-container .slide__2', {zIndex: 22, autoAlpha: 1})
        .to('.home-container .services-left', {duration: 1, autoAlpha: 0})
        .to('.home-container .services-right', {duration: 1, autoAlpha: 0}, '-=1')

        .to('.home-container .services-car__dynoflex', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-text__dynoflex', {duration: 1, autoAlpha: 0}, '-=1')
        .to('.home-container .services-features__dynoflex .feature', {duration: 0.5, stagger: 0.1, autoAlpha: 0, y: 0}, '-=1')


        .to('.home-container .car__tesla .car-services', { duration: 0.5, autoAlpha: 0, ease:'Expo.easeInOut'})
        .to('.home-container .offer-features .feature', {stagger: 0.2,duration: 1, y: 100, autoAlpha: 0}, '-=1.5')
        .to('.home-container .car__tesla', {duration: 1.75, xPercent: -136, ease:'Expo.easeInOut'}, '-=1.5')

        .to('.animated__about-subtitle', {duration: 2, autoAlpha: 1, maxWidth: '220px', ease:'Expo.easeInOut'}, '-=1')
        .to('.animated__about-title', {duration: 2, autoAlpha: 1, maxWidth: '738px', ease:'Expo.easeInOut'}, '-=2')
        .to('.animated__about-text-1', {duration: 2, autoAlpha: 1, maxWidth: '383px', ease:'Expo.easeInOut'}, '-=2')
        .to('.animated__about-text-2', {duration: 2, autoAlpha: 1, maxWidth: '292px', ease:'Expo.easeInOut'}, '-=2')
        .to('.home-container .about-bg', {duration: 1.5, autoAlpha: 1}, '-=2')

        .set('.home-container .services-items-wrapper', {y: 70})
        .set('.home-container .services-item__dynoflex', {opacity: 0.2, scale: 1})
        .set('.home-container .services-item__restorfx', {scale: 1.5, autoAlpha: 1})
        .fromTo('.home-container .about-return', {x: 100, autoAlpha: 0},{duration: 1.5, autoAlpha: 1, x: 0}, '-=1.5')
        .fromTo('.home-container .about-video', {y: 100, autoAlpha: 0},{duration: 1, autoAlpha: 1, y: 0, onComplete: () => {
            this.canAnimateSlide = true
        }}, '-=1.25')

        this.timeline_8_4
          .to('.home-container .services-items-wrapper', {duration: 1, y: 70})

          .to('.home-container .services-car__dynoflex', {duration: 1, autoAlpha: 0}, '-=1')
          .to('.home-container .services-text__dynoflex', {duration: 1, autoAlpha: 0}, '-=1')
          .to('.home-container .services-item__dynoflex', {duration: 0.5, opacity: 0.2, scale: 1}, '-=1')
          // .set('.home-container .services-features__dynoflex', {duration: 1, autoAlpha: 0}, '-=1')
          .to('.home-container .services-features__dynoflex .feature', {duration: 0.5, stagger: 0.1, autoAlpha: 0, y: 0}, '-=1')

          .to('.home-container .services-item__restorfx', {scale: 1.5, autoAlpha: 1}, '-=1')
          .to('.home-container .services-car__restorfx', {duration: 1, autoAlpha: 1}, '-=1')
          .to('.home-container .services-text__restorfx', {duration: 1, autoAlpha: 1}, '-=1')
          // .set('.home-container .services-features__restorfx', {duration: 1, autoAlpha: 1}, '-=1')
          .to('.home-container .services-features__restorfx .feature', {duration: 0.5, stagger: 0.1, autoAlpha: 1, y: -120, onComplete: () => {this.canAnimateSlide = true}}, '-=1')

        this.timeline_8_7
          .to('.home-container .services-items-wrapper', {duration: 1, y: -150}, '-=1')
          .to('.home-container .services-car__dynoflex', {duration: 1, autoAlpha: 0}, '-=1')
          .to('.home-container .services-text__dynoflex', {duration: 1, autoAlpha: 0}, '-=1')
          .to('.home-container .services-item__dynoflex', {duration: 0.5, opacity: 0.2, scale: 1}, '-=1')
          .to('.home-container .services-features__dynoflex .feature', {duration: 0.5, stagger: 0.1, autoAlpha: 0, y: 0}, '-=1')


          .to('.home-container .services-car__ppf', {duration: 1, autoAlpha: 1}, '-=1')
          .to('.home-container .services-text__ppf', {duration: 1, autoAlpha: 1}, '-=1')
          .to('.home-container .services-item__ppf', {duration: 0.5, opacity: 1, scale: 1.5}, '-=1')
          .to('.home-container .services-features__ppf .feature', {duration: 0.5, stagger: 0.1, autoAlpha: 1, y: -120, onComplete: () => {this.canAnimateSlide = true}}, '-=0.5')



         this.timeline_8_9

          .to('.home-container .services-left', {duration: 1, autoAlpha: 0})
          .to('.home-container .services-right', {duration: 1, autoAlpha: 0}, '-=1')
          .to('.home-container .services-car__dynoflex', {duration: 1, autoAlpha: 0}, '-=1')
          .to('.home-container .services-text__dynoflex', {duration: 1, autoAlpha: 0}, '-=1')
          .to('.home-container .services-item__dynoflex', {duration: 0.5, opacity: 0.2, scale: 1}, '-=1')

          .to('.home-container .services-features__dynoflex .feature', {duration: 0.5, stagger: 0.1, autoAlpha: 0, y: 0}, '-=1')


          .to('.home-container .feedback', {duration: 1, autoAlpha: 1, onComplete: () => {this.canAnimateSlide = true}})



         this.timeline_8_11

          .to('.home-container .services-left', {duration: 1, autoAlpha: 0})
          .to('.home-container .services-right', {duration: 1, autoAlpha: 0}, '-=1')
          .to('.home-container .services-car__dynoflex', {duration: 1, autoAlpha: 0}, '-=1')
          .to('.home-container .services-text__dynoflex', {duration: 1, autoAlpha: 0}, '-=1')
          .set('.home-container .services-features__dynoflex', {duration: 1, autoAlpha: 0}, '-=1')
          .to('.home-container .services-features__dynoflex .feature', {duration: 0.5, stagger: 0.1, autoAlpha: 0, y: 0}, '-=1')
          .set('.home-container .services-items-wrapper', {y: 70})
          .set('.home-container .services-item__dynoflex', {opacity: 0.2, scale: 1})
          .set('.home-container .services-item__restorfx', {scale: 1.5, autoAlpha: 1})

          .to('.home-container .contacts', {duration: 1, autoAlpha: 1, onComplete: () => {this.canAnimateSlide = true}})

        //SLIDe8 //////
        //SLIDe9 //////
        //
      this.timeline_9_1

        .to('.home-container .feedback', {duration: 1, autoAlpha: 0})


        .to('.slide .offer-sub', {duration: 1, x: 0, autoAlpha: 1})
        .to('.slide .offer-btn', {duration: 1, y: 0, autoAlpha: 1}, '-=1')
        .to('.slide .offer-title', {duration: 1, x: 0, autoAlpha: 1}, '-=1')
        .to('.slide .offer-text', {duration: 1, x: 0, autoAlpha: 1}, '-=1')
        .to('.car__tesla .car-services', { duration: 0.5, autoAlpha: 1, ease:'Expo.easeInOut'}, '-=1')
        .to('.home-container .offer-features .feature', {stagger: 0.2,duration: 1, y: 0, autoAlpha: 1}, '-=1')
        .set('.home-container .slide__1', {zIndex: 22})
        .to('.home-container .car__tesla', {duration: 2.5, xPercent: -0, ease:'Expo.easeInOut', onComplete: () => {
          this.canAnimateSlide = true
        }}, '-=2.5')

        this.timeline_9_2
          .set('.home-container .slide__2', {zIndex: 22, autoAlpha: 1})
          .to('.home-container .feedback', {duration: 1, autoAlpha: 0})
          .to('.home-container .car__tesla .car-services', { duration: 0.5, autoAlpha: 0, ease:'Expo.easeInOut'})
          .to('.home-container .offer-features .feature', {stagger: 0.2,duration: 1, y: 100, autoAlpha: 0}, '-=1.5')
          .to('.home-container .car__tesla', {duration: 1.75, xPercent: -136, ease:'Expo.easeInOut'}, '-=1.5')

          .to('.animated__about-subtitle', {duration: 2, autoAlpha: 1, maxWidth: '220px', ease:'Expo.easeInOut'}, '-=1')
          .to('.animated__about-title', {duration: 2, autoAlpha: 1, maxWidth: '738px', ease:'Expo.easeInOut'}, '-=2')
          .to('.animated__about-text-1', {duration: 2, autoAlpha: 1, maxWidth: '383px', ease:'Expo.easeInOut'}, '-=2')
          .to('.animated__about-text-2', {duration: 2, autoAlpha: 1, maxWidth: '292px', ease:'Expo.easeInOut'}, '-=2')
          .to('.home-container .about-bg', {duration: 1.5, autoAlpha: 1}, '-=2')

          .set('.home-container .services-items-wrapper', {y: 70})
          .set('.home-container .services-item__dynoflex', {opacity: 0.2, scale: 1})
          .set('.home-container .services-item__restorfx', {scale: 1.5, autoAlpha: 1})
          .fromTo('.home-container .about-return', {x: 100, autoAlpha: 0},{duration: 1.5, autoAlpha: 1, x: 0}, '-=1.5')
          .fromTo('.home-container .about-video', {y: 100, autoAlpha: 0},{duration: 1, autoAlpha: 1, y: 0, onComplete: () => {
              this.canAnimateSlide = true
          }}, '-=1.25')

        this.timeline_9_4
          .set('.home-container .services-item__restorfx', {scale: 1.5, autoAlpha: 1})

          .to('.home-container .feedback', {duration: 1, autoAlpha: 0})
          .to('.home-container .services-items-wrapper', {duration: 1, y: 70}, '-=1')
          .to('.home-container .services-left', {duration: 1, autoAlpha: 1})
          .to('.home-container .services-right', {duration: 1, autoAlpha: 1}, '-=1')
          .to('.home-container .services-car__restorfx', {duration: 1, autoAlpha: 1}, '-=1')
          .to('.home-container .services-text__restorfx', {duration: 1, autoAlpha: 1}, '-=1')
          // .to('.home-container .services-item__restorfx', {duration: 1, autoAlpha: 0.2}, '-=1')
          .set('.home-container .services-features__restorfx', {duration: 1, autoAlpha: 1}, '-=1')
          .to('.home-container .services-features__restorfx .feature', {duration: 0.5, stagger: 0.1, autoAlpha: 1, y: -120, onComplete: () => {this.canAnimateSlide = true}}, '-=1')


        // this.timeline_9_10 //feedback to map (9 to 10)
        // .to('.home-container .feedback', {duration: 1, autoAlpha: 0})
        // .to('.home-container .map', {duration: 1, autoAlpha: 1, onComplete: () => {this.canAnimateSlide = true}})


        this.timeline_9_8 //feedback to map (9 to 10)

          .to('.home-container .feedback', {duration: 1, autoAlpha: 0})

          .set('.home-container .services-item__restorfx', {duration: 0.5, opacity: 0.2, scale: 1}, '-=1')
          .set('.home-container .services-item__dynoflex', {duration: 0.5, opacity: 1, scale: 1.5}, '-=1')
          .to('.home-container .services-items-wrapper', {duration: 1, y: -225}, '-=1')
          .to('.home-container .services-left', {duration: 1, autoAlpha: 1})
          .to('.home-container .services-right', {duration: 1, autoAlpha: 1}, '-=1')
          .set('.home-container .services-features__dynoflex', {duration: 1, autoAlpha: 1}, '-=1')
          .to('.home-container .services-car__dynoflex', {duration: 1, autoAlpha: 1}, '-=1')
          .to('.home-container .services-text__dynoflex', {duration: 1, autoAlpha: 1}, '-=1')
          .to('.home-container .services-features__dynoflex .feature', {duration: 0.5, stagger: 0.1, autoAlpha: 1, y: -120, onComplete: () => {this.canAnimateSlide = true}}, '-=1')


        this.timeline_9_10 //feedback to map (9 to 10)

          .to('.home-container .feedback', {duration: 1, autoAlpha: 0})

          .to('.home-container .map', {duration: 1, autoAlpha: 1, onComplete: () => {this.canAnimateSlide = true}})

        this.timeline_9_11 //feedback to map (9 to 10)

          .to('.home-container .feedback', {duration: 1, autoAlpha: 0})
          .to('.home-container .contacts', {duration: 1, autoAlpha: 1, onComplete: () => {this.canAnimateSlide = true}})

          //SLIDe9 //////
          //SLIDe10//////


      this.timeline_10_1

        .to('.home-container .map', {duration: 1, autoAlpha: 0})


        .to('.slide .offer-sub', {duration: 1, x: 0, autoAlpha: 1})
        .to('.slide .offer-btn', {duration: 1, y: 0, autoAlpha: 1}, '-=1')
        .to('.slide .offer-title', {duration: 1, x: 0, autoAlpha: 1}, '-=1')
        .to('.slide .offer-text', {duration: 1, x: 0, autoAlpha: 1}, '-=1')
        .to('.car__tesla .car-services', { duration: 0.5, autoAlpha: 1, ease:'Expo.easeInOut'}, '-=1')
        .to('.home-container .offer-features .feature', {stagger: 0.2,duration: 1, y: 0, autoAlpha: 1}, '-=1')
        .set('.home-container .slide__1', {zIndex: 22})
        .to('.home-container .car__tesla', {duration: 2.5, xPercent: -0, ease:'Expo.easeInOut', onComplete: () => {
          this.canAnimateSlide = true
        }}, '-=2.5')



        this.timeline_10_2 //map to contacts (10 to 11)
          .set('.home-container .slide__2', {zIndex: 22, autoAlpha: 1})

          .to('.home-container .map', {duration: 1, autoAlpha: 0})
          .to('.home-container .car__tesla .car-services', { duration: 0.5, autoAlpha: 0, ease:'Expo.easeInOut'})
          .to('.home-container .offer-features .feature', {stagger: 0.2,duration: 1, y: 100, autoAlpha: 0}, '-=1.5')
          .to('.home-container .car__tesla', {duration: 1.75, xPercent: -136, ease:'Expo.easeInOut'}, '-=1.5')

          .to('.animated__about-subtitle', {duration: 2, autoAlpha: 1, maxWidth: '220px', ease:'Expo.easeInOut'}, '-=1')
          .to('.animated__about-title', {duration: 2, autoAlpha: 1, maxWidth: '738px', ease:'Expo.easeInOut'}, '-=2')
          .to('.animated__about-text-1', {duration: 2, autoAlpha: 1, maxWidth: '383px', ease:'Expo.easeInOut'}, '-=2')
          .to('.animated__about-text-2', {duration: 2, autoAlpha: 1, maxWidth: '292px', ease:'Expo.easeInOut'}, '-=2')
          .to('.home-container .about-bg', {duration: 1.5, autoAlpha: 1}, '-=2')

          .set('.home-container .services-items-wrapper', {y: 70})
          .set('.home-container .services-item__dynoflex', {opacity: 0.2, scale: 1})
          .set('.home-container .services-item__restorfx', {scale: 1.5, autoAlpha: 1})
          .fromTo('.home-container .about-return', {x: 100, autoAlpha: 0},{duration: 1.5, autoAlpha: 1, x: 0}, '-=1.5')
          .fromTo('.home-container .about-video', {y: 100, autoAlpha: 0},{duration: 1, autoAlpha: 1, y: 0, onComplete: () => {
              this.canAnimateSlide = true
          }}, '-=1.25')

        this.timeline_10_4 //map to contacts (10 to 11)
          .set('.home-container .services-item__restorfx', {scale: 1.5, autoAlpha: 1})
          .to('.home-container .map', {duration: 1, autoAlpha: 0})

          .to('.home-container .services-items-wrapper', {duration: 1, y: 70}, '-=1')
          .to('.home-container .services-left', {duration: 1, autoAlpha: 1})
          .to('.home-container .services-right', {duration: 1, autoAlpha: 1}, '-=1')
          .to('.home-container .services-car__restorfx', {duration: 1, autoAlpha: 1}, '-=1')
          .to('.home-container .services-text__restorfx', {duration: 1, autoAlpha: 1}, '-=1')
          // .to('.home-container .services-item__restorfx', {duration: 1, autoAlpha: 0.2}, '-=1')
          .set('.home-container .services-features__restorfx', {duration: 1, autoAlpha: 1}, '-=1')
          .to('.home-container .services-features__restorfx .feature', {duration: 0.5, stagger: 0.1, autoAlpha: 1, y: -120, onComplete: () => {this.canAnimateSlide = true}}, '-=1')


        this.timeline_10_9 //map to contacts (10 to 11)

          .to('.home-container .map', {duration: 1, autoAlpha: 0})
          .to('.home-container .feedback', {duration: 1, autoAlpha: 1, onComplete: () => {this.canAnimateSlide = true}})


        this.timeline_10_11 //map to contacts (10 to 11)

          .to('.home-container .map', {duration: 1, autoAlpha: 0})
          .to('.home-container .contacts', {duration: 1, autoAlpha: 1, onComplete: () => {this.canAnimateSlide = true}})

        ///////////////
        ///////////////
        ///////////////
        ///
      this.timeline_11_1

        .to('.home-container .contacts', {duration: 1, autoAlpha: 0})


        .to('.slide .offer-sub', {duration: 1, x: 0, autoAlpha: 1})
        .to('.slide .offer-btn', {duration: 1, y: 0, autoAlpha: 1}, '-=1')
        .to('.slide .offer-title', {duration: 1, x: 0, autoAlpha: 1}, '-=1')
        .to('.slide .offer-text', {duration: 1, x: 0, autoAlpha: 1}, '-=1')
        .to('.car__tesla .car-services', { duration: 0.5, autoAlpha: 1, ease:'Expo.easeInOut'}, '-=1')
        .to('.home-container .offer-features .feature', {stagger: 0.2,duration: 1, y: 0, autoAlpha: 1}, '-=1')
        .set('.home-container .slide__1', {zIndex: 22})
        .to('.home-container .car__tesla', {duration: 2.5, xPercent: -0, ease:'Expo.easeInOut', onComplete: () => {
          this.canAnimateSlide = true
        }}, '-=2.5')

         this.timeline_11_2 //map to contacts (10 to 11)
          .set('.home-container .slide__2', {zIndex: 22, autoAlpha: 1})

          .to('.home-container .contacts', {duration: 1, autoAlpha: 0})
          .to('.home-container .car__tesla .car-services', { duration: 0.5, autoAlpha: 0, ease:'Expo.easeInOut'})
          .to('.home-container .offer-features .feature', {stagger: 0.2,duration: 1, y: 100, autoAlpha: 0}, '-=1.5')
          .to('.home-container .car__tesla', {duration: 1.75, xPercent: -136, ease:'Expo.easeInOut'}, '-=1.5')

          .to('.animated__about-subtitle', {duration: 2, autoAlpha: 1, maxWidth: '220px', ease:'Expo.easeInOut'}, '-=1')
          .to('.animated__about-title', {duration: 2, autoAlpha: 1, maxWidth: '738px', ease:'Expo.easeInOut'}, '-=2')
          .to('.animated__about-text-1', {duration: 2, autoAlpha: 1, maxWidth: '383px', ease:'Expo.easeInOut'}, '-=2')
          .to('.animated__about-text-2', {duration: 2, autoAlpha: 1, maxWidth: '292px', ease:'Expo.easeInOut'}, '-=2')
          .to('.home-container .about-bg', {duration: 1.5, autoAlpha: 1}, '-=2')

          .set('.home-container .services-items-wrapper', {y: 70})
          .set('.home-container .services-item__dynoflex', {opacity: 0.2, scale: 1})
          .set('.home-container .services-item__restorfx', {scale: 1.5, autoAlpha: 1})
          .fromTo('.home-container .about-return', {x: 100, autoAlpha: 0},{duration: 1.5, autoAlpha: 1, x: 0}, '-=1.5')
          .fromTo('.home-container .about-video', {y: 100, autoAlpha: 0},{duration: 1, autoAlpha: 1, y: 0, onComplete: () => {
              this.canAnimateSlide = true
          }}, '-=1.25')

        this.timeline_11_4 //map to contacts (10 to 11)
          .set('.home-container .services-item__restorfx', {scale: 1.5, autoAlpha: 1})

          .to('.home-container .contacts', {duration: 1, autoAlpha: 0})
          .to('.home-container .services-items-wrapper', {duration: 1, y: 70}, '-=1')
          .to('.home-container .services-left', {duration: 1, autoAlpha: 1})
          .to('.home-container .services-right', {duration: 1, autoAlpha: 1}, '-=1')
          .to('.home-container .services-car__restorfx', {duration: 1, autoAlpha: 1}, '-=1')
          .to('.home-container .services-text__restorfx', {duration: 1, autoAlpha: 1}, '-=1')
          // .to('.home-container .services-item__restorfx', {duration: 1, autoAlpha: 0.2}, '-=1')
          .set('.home-container .services-features__restorfx', {duration: 1, autoAlpha: 1}, '-=1')
          .to('.home-container .services-features__restorfx .feature', {duration: 0.5, stagger: 0.1, autoAlpha: 1, y: -120, onComplete: () => {this.canAnimateSlide = true}}, '-=1')


        this.timeline_11_9 //map to contacts (10 to 11)

          .to('.home-container .contacts', {duration: 1, autoAlpha: 0})
          .to('.home-container .feedback', {duration: 1, autoAlpha: 1, onComplete: () => {this.canAnimateSlide = true}})


        this.timeline_11_10 //map to contacts (10 to 11)

          .to('.home-container .contacts', {duration: 1, autoAlpha: 0})
          .to('.home-container .map', {duration: 1, autoAlpha: 1, onComplete: () => {this.canAnimateSlide = true}})

  },
  methods: {
    initMap(){
      this.map = new window.google.maps.Map(document.querySelector('.google_map'), {
        center: {
          lat: 41.9770496,
          lng: -87.9649508
        },
        zoom: 11,
        styles: [{
            "elementType": "geometry",
            "stylers": [{
              "color": "#212121"
            }]
          },
          {
            "elementType": "labels.icon",
            "stylers": [{
              "visibility": "off"
            }]
          },
          {
            "elementType": "labels.text.fill",
            "stylers": [{
              "color": "#757575"
            }]
          },
          {
            "elementType": "labels.text.stroke",
            "stylers": [{
              "color": "#212121"
            }]
          },
          {
            "featureType": "administrative",
            "elementType": "geometry",
            "stylers": [{
              "color": "#757575"
            }]
          },
          {
            "featureType": "administrative.country",
            "elementType": "labels.text.fill",
            "stylers": [{
              "color": "#9e9e9e"
            }]
          },
          {
            "featureType": "administrative.land_parcel",
            "stylers": [{
              "visibility": "off"
            }]
          },
          {
            "featureType": "administrative.locality",
            "elementType": "labels.text.fill",
            "stylers": [{
              "color": "#bdbdbd"
            }]
          },
          {
            "featureType": "poi",
            "elementType": "labels.text.fill",
            "stylers": [{
              "color": "#757575"
            }]
          },
          {
            "featureType": "poi.park",
            "elementType": "geometry",
            "stylers": [{
              "color": "#181818"
            }]
          },
          {
            "featureType": "poi.park",
            "elementType": "labels.text.fill",
            "stylers": [{
              "color": "#616161"
            }]
          },
          {
            "featureType": "poi.park",
            "elementType": "labels.text.stroke",
            "stylers": [{
              "color": "#1b1b1b"
            }]
          },
          {
            "featureType": "road",
            "elementType": "geometry.fill",
            "stylers": [{
              "color": "#2c2c2c"
            }]
          },
          {
            "featureType": "road",
            "elementType": "labels.text.fill",
            "stylers": [{
              "color": "#8a8a8a"
            }]
          },
          {
            "featureType": "road.arterial",
            "elementType": "geometry",
            "stylers": [{
              "color": "#373737"
            }]
          },
          {
            "featureType": "road.highway",
            "elementType": "geometry",
            "stylers": [{
              "color": "#3c3c3c"
            }]
          },
          {
            "featureType": "road.highway.controlled_access",
            "elementType": "geometry",
            "stylers": [{
              "color": "#4e4e4e"
            }]
          },
          {
            "featureType": "road.local",
            "elementType": "labels.text.fill",
            "stylers": [{
              "color": "#616161"
            }]
          },
          {
            "featureType": "transit",
            "elementType": "labels.text.fill",
            "stylers": [{
              "color": "#757575"
            }]
          },
          {
            "featureType": "water",
            "elementType": "geometry",
            "stylers": [{
              "color": "#000000"
            }]
          },
          {
            "featureType": "water",
            "elementType": "labels.text.fill",
            "stylers": [{
              "color": "#3d3d3d"
            }]
          }
        ]
      });
      this.marker = new window.google.maps.Marker({
        map: this.map,
        position: new window.google.maps.LatLng(41.9770496,-87.9649508),
        // title: "Hello WOrld",
        icon: {
          url: '/assets/img/map-marker.svg',
          scaledSize: {width: 33, height: 33},
          labelOrigin: {x: 16, y: -10}
        },
        clickable: true
      })
      this.infowindow = new window.google.maps.InfoWindow({
        content: "Restor FX",
        backgroundColor: 'rgb(57,57,57)',
      });
      this.infowindow.open(this.map, this.marker);
      this.mobileMap = new window.google.maps.Map(document.querySelector('.map-map'), {
        center: {
          lat: 41.9770496,
          lng: -88.2451022
        },
        zoom: 11,
        styles: [{
            "elementType": "geometry",
            "stylers": [{
              "color": "#212121"
            }]
          },
          {
            "elementType": "labels.icon",
            "stylers": [{
              "visibility": "off"
            }]
          },
          {
            "elementType": "labels.text.fill",
            "stylers": [{
              "color": "#757575"
            }]
          },
          {
            "elementType": "labels.text.stroke",
            "stylers": [{
              "color": "#212121"
            }]
          },
          {
            "featureType": "administrative",
            "elementType": "geometry",
            "stylers": [{
              "color": "#757575"
            }]
          },
          {
            "featureType": "administrative.country",
            "elementType": "labels.text.fill",
            "stylers": [{
              "color": "#9e9e9e"
            }]
          },
          {
            "featureType": "administrative.land_parcel",
            "stylers": [{
              "visibility": "off"
            }]
          },
          {
            "featureType": "administrative.locality",
            "elementType": "labels.text.fill",
            "stylers": [{
              "color": "#bdbdbd"
            }]
          },
          {
            "featureType": "poi",
            "elementType": "labels.text.fill",
            "stylers": [{
              "color": "#757575"
            }]
          },
          {
            "featureType": "poi.park",
            "elementType": "geometry",
            "stylers": [{
              "color": "#181818"
            }]
          },
          {
            "featureType": "poi.park",
            "elementType": "labels.text.fill",
            "stylers": [{
              "color": "#616161"
            }]
          },
          {
            "featureType": "poi.park",
            "elementType": "labels.text.stroke",
            "stylers": [{
              "color": "#1b1b1b"
            }]
          },
          {
            "featureType": "road",
            "elementType": "geometry.fill",
            "stylers": [{
              "color": "#2c2c2c"
            }]
          },
          {
            "featureType": "road",
            "elementType": "labels.text.fill",
            "stylers": [{
              "color": "#8a8a8a"
            }]
          },
          {
            "featureType": "road.arterial",
            "elementType": "geometry",
            "stylers": [{
              "color": "#373737"
            }]
          },
          {
            "featureType": "road.highway",
            "elementType": "geometry",
            "stylers": [{
              "color": "#3c3c3c"
            }]
          },
          {
            "featureType": "road.highway.controlled_access",
            "elementType": "geometry",
            "stylers": [{
              "color": "#4e4e4e"
            }]
          },
          {
            "featureType": "road.local",
            "elementType": "labels.text.fill",
            "stylers": [{
              "color": "#616161"
            }]
          },
          {
            "featureType": "transit",
            "elementType": "labels.text.fill",
            "stylers": [{
              "color": "#757575"
            }]
          },
          {
            "featureType": "water",
            "elementType": "geometry",
            "stylers": [{
              "color": "#000000"
            }]
          },
          {
            "featureType": "water",
            "elementType": "labels.text.fill",
            "stylers": [{
              "color": "#3d3d3d"
            }]
          }
        ]
      });
      this.mobileMarker =new window.google.maps.Marker({
        map: this.mobileMap,
        position:new window.google.maps.LatLng(41.9770496,-87.9649508),
        icon: {
          url: '/assets/img/map-marker.svg',
          scaledSize: {width: 33, height: 33},
          labelOrigin: {x: 16, y: -10}
        },
        clickable: true
      })
      this.mobileInfowindow = new window.google.maps.InfoWindow({
        content: "Restor FX",
        backgroundColor: 'rgb(57,57,57)',
      });
      this.mobileInfowindow.open(this.mobileMap, this.mobileMarker);
      this.infowindow.open(this.map, this.marker);

    },
    editReviewsSlider() {
      for(let i = 0; i < this.wpData.feedback_reviews.length; i+=2){

        if(this.wpData.feedback_reviews[i+1]){
        this.desktopReviewsSlider.push({
          service1: this.wpData.feedback_reviews[i].service,
          name1: this.wpData.feedback_reviews[i].name,
          text1: this.wpData.feedback_reviews[i].text,
          service2: this.wpData.feedback_reviews[i+1].service,
          name2: this.wpData.feedback_reviews[i+1].name,
          text2: this.wpData.feedback_reviews[i+1].text
        })

        } else {
          // this.desktopReviewsSlider.push({
          //   service1: this.reviewsSlider[i].service,
          //   name1: this.reviewsSlider[i].name,
          //   text1: this.reviewsSlider[i].text,
          // })
        }
      }
    },
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
    animateSlideByClick(slide, event){
      if(this.canAnimateSlide) {
        this.prevSlide = this.currentSlide;
        this.currentSlide = slide;
      }
    },
    animateSlide(event){
      if(event.target.closest('#google_map')){
        return
      }
      if(this.canAnimateSlide) {
        this.prevSlide = this.currentSlide
        if(event.deltaY < 0){
          if(this.currentSlide != 1) {

            this.currentSlide -= 1
            this.canAnimateSlide = false
          }
        } else {
          if(this.currentSlide >= 11) {
            this.currentSlide = 11
          } else {
            this.currentSlide += 1
            this.canAnimateSlide = false

          }
        }

      }
    },
    scrollToSection(event) {
      this.showMenu = false;
      const sectionToScrollId = '#'+event.currentTarget.dataset.slideto;
      const headerHeight = document.querySelector('.fixed-header').offsetHeight;
      const offsetTop = document.querySelector(sectionToScrollId).offsetTop - headerHeight
      window.scrollTo({
        top: offsetTop,
        left: 0,
        behavior: 'smooth'
      });
    },

    contactFormSubmit(values, actions) {
      actions.resetForm();
      this.$router.push({ name: "Thanks"})
    },
    validateRequired(value) {
      if(!value) return 'This field is required'
      return true;
    },
    hideVideo(event) {
      this.showVideo = false
    },
    bodyPopupStyles(someVar) {
      this.scrollWidth = window.innerWidth - document.body.offsetWidth
      document.body.style.overflow = someVar ? 'hidden' : 'auto'
      document.body.style.paddingRight = someVar ? this.scrollWidth + 'px' : '0px'
    },

    getWordpressData(){
      // fetch("https://admin.restor-chicago.com/wp-json/markers/v1/post", {
      fetch("http://sub.restor.server/wp-json/markers/v1/post", {
        method: 'GET',
        // body: formData
      })
      .then(data => {
        return data.json();
      })
      .then(response => {
        console.log(response)
        this.wpData = response;
        this.editReviewsSlider();
      })
    },
  },
  watch: {

    currentSlide: function() {
      // this.prevSlide = this.currentSlide;
      switch (this.prevSlide) {
        case 1:
          switch(this.currentSlide){
            case 2:
              this.timeline_1_2.restart();
              break; ////////////////////////READY
            case 4:
              this.timeline_1_4.restart();
              break; ////////////////////////READY
            case 9:
              this.timeline_1_9.restart();
              break; ////////////////////////READY
            case 11:
              this.timeline_1_11.restart();
              break; ////////////////////////READY
          }
          break;
        case 2:
          switch(this.currentSlide){
            case 1:
              this.timeline_2_1.restart();
              break; ////////////////////READY
            case 3:
              this.timeline_2_3.restart();
              break; ////////////////////READY
            case 4:
              this.timeline_2_4.restart();
              break; ////////////////////READY
            case 9:
              this.timeline_2_9.restart();
              break;  ///////////////////READY
            case 11:
              this.timeline_2_11.restart();
              break;  ///////////////////READY
          }
          break;
        case 3:
          switch(this.currentSlide){
            case 1:
              this.timeline_3_1.restart();
              break; ////////////////////READY
            case 2:
              this.timeline_3_2.restart();
              break; ////////////////////READY
            case 4:
              this.timeline_3_4.restart();
              break; ////////////////////READY
            case 9:
              this.timeline_3_9.restart();
              break;  ///////////////////READY
            case 11:
              this.timeline_3_11.restart();
              break;  ///////////////////READY
          }
          break;
        case 4:
          switch(this.currentSlide){
            case 1:
              this.timeline_4_1.restart();
              break; ////////////////////READY

            case 2:
              this.timeline_4_2.restart();
              break; ////////////////////READY
            case 3:
              this.timeline_4_3.restart();
              break; ////////////////////READY
            case 5:
              this.timeline_4_5.restart();
              break;   ////////////////////READY
            case 9:
              this.timeline_4_9.restart();
              break;  ////////////////////READY
            case 11:
              this.timeline_4_11.restart();
              break;  ////////////////////READY
          }
          break;
        case 5:
          switch(this.currentSlide){
            case 1:
              this.timeline_5_1.restart();
              break; ////////////////////READY
            case 2:
              this.timeline_5_2.restart();
              break; ////////// READY
            case 4:
              this.timeline_5_4.restart();
              break; ///////// READY
            case 6:
              this.timeline_5_6.restart();
              break; ///////// READY
            case 9:
              this.timeline_5_9.restart();
              break;
            case 11:
              this.timeline_5_11.restart();
              break;
          }
          break;
        case 6:
          switch(this.currentSlide){
            case 1:
              this.timeline_6_1.restart();
              break; ////////////////////READY
            case 2:
              this.timeline_6_2.restart();
              break; ////////// READY
            case 4:
              this.timeline_6_4.restart();
              break; /////// READY
            case 5:
              this.timeline_6_5.restart();
              break; //////READY
            case 7:
              this.timeline_6_7.restart();
              break; //////READY
            case 9:
              this.timeline_6_9.restart();
              break;  //////READY
            case 11:
              this.timeline_6_11.restart();
              break;  //////READY
            }
          break;
        case 7:
          switch(this.currentSlide){
            case 1:
              this.timeline_7_1.restart();
              break; ////////////////////READY
            case 2:
              this.timeline_7_2.restart();
              break; // OKKOKOKOKOKOKOK
            case 4:
              this.timeline_7_4.restart();
              break; // READY
            case 6:
              this.timeline_7_6.restart();
              break; // READY
            case 8:
              this.timeline_7_8.restart();
              break; // READY
            case 9:
              this.timeline_7_9.restart();
              break;  // READY
            case 11:
              this.timeline_7_11.restart();
              break;  // READY
          }
          break;
        case 8:
          switch(this.currentSlide){
            case 1:
              this.timeline_8_1.restart();
              break; ////////////////////READY
            case 2:
              this.timeline_8_2.restart();
              break; //ok
            case 4:
              this.timeline_8_4.restart();
              break; //ok
            case 7:
              this.timeline_8_7.restart();
              break; //ok
            case 9:
              this.timeline_8_9.restart();
              break; //ok
            case 11:
              this.timeline_8_11.restart();
              break;  //ok
          }
          break;
        case 9:
          switch(this.currentSlide){
            case 1:
              this.timeline_9_1.restart();
              break; ////////////////////READY
            case 2:
              this.timeline_9_2.restart();
              break; //ok
            case 4:
              this.timeline_9_4.restart();
              break;  //ok
            case 8:
              this.timeline_9_8.restart();
              break; //ok
            case 10:
              this.timeline_9_10.restart();
              break; //ok
            case 11:
              this.timeline_9_11.restart();
              break;  //ok
          }
          break;
        case 10:
          switch(this.currentSlide){
            case 1:
              this.timeline_10_1.restart();
              break; ////////////////////READY
            case 2:
              this.timeline_10_2.restart();
              break; //ok
            case 4:
              this.timeline_10_4.restart();
              break;  //ok
            case 9:
              this.timeline_10_9.restart();
              break; //ok
            case 11:
              this.timeline_10_11.restart();
              break; //ok
          }
          break;
        case 11:
          switch(this.currentSlide){
            case 1:
              this.timeline_11_1.restart();
              break; ////////////////////READY
            case 2:
              this.timeline_11_2.restart();
              break; //ok
            case 4:
              this.timeline_11_4.restart();
              break;  //ok
            case 9:
              this.timeline_11_9.restart();
              break; //ok
            case 10:
              this.timeline_11_10.restart();
              break; //ok
          }
          break;
        default:
          break;
      }



    },
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
  directives: {
    sticky: {
      mounted(el, binding) {
        if(window.pageYOffset > 1000){
          el.classList.add('active')
          el.style.transform = 'translateY(0)'
        } else {
          el.style.transform = 'translateY(-100%)'
        }
        window.addEventListener('scroll', function(){
          if(window.pageYOffset > 1000){
            el.classList.add('active')
            el.style.transform = 'translateY(0)'

          } else {
            el.style.transform = 'translateY(-100%)'
          }
        })

      }
    }
  },
  created() {
    this.getWordpressData();
    // this.initMap()
    // this.wrapperFunc();
    document.title = "Restor FX";
  },
};
</script>

<style lang="sass">

.slideout-enter-active,
.slideout-leave-active
  transition: transform 0.5s ease


.slideout-enter-from,
.slideout-leave-to
  transform: translateY(-100%)

.fadeIn-enter-active,
.fadeIn-leave-active
  transition: opacity 0.2s ease


.fadeIn-enter-from,
.fadeIn-leave-to
  opacity: 0

@font-face
  font-family: 'PilatExtended-Book'
  font-style: normal
  font-display: auto
  src: url("/assets/fonts/PilatExtended-Book.ttf") format("truetype"), url("/assets/fonts/PilatExtended-Book.woff") format("woff"), url("/assets/fonts/PilatExtended-Book.woff2") format("woff2")
@font-face
  font-family: "PilatExtended-DemiBold"
  font-style: normal
  font-display: auto
  src: url("/assets/fonts/PilatExtended-DemiBold.ttf") format("truetype"), url("/assets/fonts/PilatExtended-DemiBold.woff") format("woff"), url("/assets/fonts/PilatExtended-DemiBold.woff2") format("woff2")
@font-face
  font-family: "PilatExtended-Heavy"
  font-style: normal
  font-display: auto
  src: url("/assets/fonts/PilatExtended-Heavy.ttf") format("truetype"), url("/assets/fonts/PilatExtended-Heavy.woff") format("woff"), url("/assets/fonts/PilatExtended-Heavy.woff2") format("woff2")
@font-face
  font-family: "roadrage"
  font-style: normal
  font-display: auto
  src: url("/assets/fonts/roadrage.ttf") format("truetype"), url("/assets/fonts/roadrage.woff") format("woff"), url("/assets/fonts/roadrage.woff2") format("woff2")
</style>