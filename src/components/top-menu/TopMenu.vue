<template>
  <header class="tdp_header">
    <router-link to="/" class="tdp_header-link">
      <img
        src="../../assets/logo.png"
        alt="Main logo of the Dark Palace"
        class="tdp_header-logo"
      />

      <h1 class="tdp_header-title">The Dark Palace</h1>
    </router-link>

    <div class="tdp_menu-container" :class="{ 'tdp_is-opened': isMenuOpened }">
      <button
        type="button"
        class="tdp_button tdp_hidden-large"
        @click="toggleMenu()"
      >
        <span class="tdp_arrow-button_inner">Main Button</span>
      </button>
      <div class="tdp_main-menu_title">Main Menu</div>
      <nav class="tdp_main-menu">
        <ul>
          <li class="tdp_main-menu_items">
            <a href="/">Home</a>
          </li>
          <li class="tdp_main-menu_items">
            <a href="/">Search</a>
          </li>
          <li class="tdp_main-menu_items">
            <a href="/">Profile</a>
          </li>
          <li class="tdp_main-menu_items">
            <a href="/">Preferences</a>
          </li>
          <li class="tdp_main-menu_items">
            <a href="/">Logout</a>
          </li>
        </ul>
      </nav>
    </div>
    <div class="tdp_overlay tdp_hidden-large" @click="toggleMenu()"></div>
  </header>
</template>

<script>
export default {
  name: "TopMenu",
  data: function () {
    return {
      isMenuOpened: false,
    };
  },
  methods: {
    toggleMenu: function () {
      this.isMenuOpened = !this.isMenuOpened;
    },
  },
};
</script>

<style lang="sass">
.tdp_header
  display: flex
  position: relative
  justify-content: space-between
  flex-wrap: wrap

.tdp_header-link
  display: flex
  align-items: center
  padding: 2vw

.tdp_header-logo
  max-width: 15vw

.tdp_header-title
  font-size: 7vw
  margin: 0 2.5vw

.tdp_menu-container
  display: flex
  align-content: flex-start
  flex-wrap: wrap
  position: absolute
  width: 17vw
  height: 17vw
  top: 0
  right: 0
  background-color: #07001E
  overflow: hidden
  transition: width 500ms ease, height 250ms ease
  will-change: height, width
  z-index: 10

  + .tdp_overlay
    position: absolute
    width: 0
    height: 100vh
    top: 0
    right: 0
    background-color: rgba(215, 150, 255, 0)
    transition: background-color 500ms ease

  &.tdp_is-opened
    width: 90vw
    height: 100vh

    + .tdp_overlay
      width: 100vw
      background-color: rgba(215, 150, 255, .75)

.tdp_button
  position: relative
  width: 15vw
  height: 15vw
  background: #E10000
  border: none
  padding: 2.5vw
  margin: 1vw
  font-size: 0

  .tdp_arrow-button_inner
    position: absolute
    width: calc(100% - 5vw)
    height: 1vw
    top: calc(50% - .5vw)
    left: 2.5vw
    background-color: white
    border-radius: .5vw

    &::before,
    &::after
      content: ""
      position: absolute
      width: 100%
      height: 1vw
      left: 0
      background-color: white
      border-radius: .5vw

    &::before
      top: 2.5vw
      transition: top 300ms ease, transform 300ms cubic-bezier(.895,.03,.685,.22) .1s

    &::after
      bottom: 2.5vw
      transition: bottom 300ms ease,transform 300ms cubic-bezier(.895,.03,.685,.22) .1s

  .tdp_is-opened & .tdp_arrow-button_inner
    &::before
      top: 0
      transform: translate3d(2.5vw,-2.5vw,0) rotate(45deg) scaleX(.75)

    &::after
      bottom: 0
      transform: translate3d(2.5vw,2.5vw,0) rotate(-45deg) scaleX(.75)

.tdp_main-menu_title
  padding: 2.5vw 7.5vw
  font-size: 2em
  font-weight: 500

.tdp_main-menu
  width: 100%

  ul
    margin: 5vw 0 0
    padding: 0
    list-style: none

.tdp_main-menu_items
  a
    display: block
    padding: 2.5vw 5vw
    color: white
</style>
