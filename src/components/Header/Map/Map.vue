<template>
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
</template>

<script>
export default {};
</script>

<style lang="sass">
.header-map
  div
    display: flex
  &-icon
    margin-right: 13px

  &-text
    color: $gray
    text-transform: uppercase
    font-size: 14px
    +tit
    line-height: 21px
</style>