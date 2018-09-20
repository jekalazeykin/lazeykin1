<template>
<div class="header">
  <div class="small__menu" @click="showMenu=!showMenu">
    <img src="../assets/menu-button-of-three-horizontal-lines.svg" alt="menu">
  </div>
  <aside :class="!showMenu?'small__menu_body':'small__menu_body small__menu_body-active'">
    <ul class="small__menu_list">
      <li v-for="(item, index) in menu" class="small__menu_list-item"><a v-bind:href="'#' + href[index]" class="menu__link" :key="item">{{item}}</a></li>
    </ul>
  </aside>
  <p class="logo">{{logo}}</p>
  <ul class="menu">
    <li v-for="(item, index) in menu" class="menu__item"><a v-bind:href="'#' + href[index]" class="menu__link" :key="item">{{item}}</a></li>
  </ul>
  <div class="search__icon">
    <img src="../assets/magnifying-glass-icon.svg" alt="search">
  </div>
</div>
</template>

<script>
export default {
  name: 'Header',
  data() {
    return {
      menu: ['HOME', 'ABOUT US', 'NEWS', 'CONTACT'],
      href: ['home', 'about', 'news', 'contact'],
      logo: 'collider',
      showMenu: false
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import url('https://fonts.googleapis.com/css?family=Fjalla+One');
.header {
  position: fixed;
  top: 0;
  width: 100vw;
  height: 6vh;
  padding: 3vh 0 2vh;
  box-shadow: inset 0px 0px 0px 2px #e9ef3b;
  color: #fff;
  background-color: #191919;
  z-index: 10;
}

.menu {
  position: absolute;
  right: 30vw;
  display: flex;
  list-style: none;
  margin: 0
}

.menu__item {
  padding-right: 15px;
}

.menu__link {
  color: #fff;
  text-decoration: none;
}

.logo {
  font-family: 'Fjalla One', sans-serif;
  text-transform: uppercase;
  font-size: 1.6em;
  position: absolute;
  left: 10vw;
  margin: 0;
}

.search__icon {
  position: absolute;
  right: 5vw;
  width: 25px;
  height: 25px;
}

.small__menu {
  position: absolute;
  left: 5px;
  top: 16px;
  cursor: pointer;
  display: none;
}

.small__menu_body {
  position: absolute;
  left: 0;
  top: 11vh;
  height: 76vh;
  background-color: #000;
  display: none;
  transform: translate(-100%);
  transition: all .3s cubic-bezier(.65, .05, .36, 1);
  border: 2px solid #eac02a;
}

.small__menu_body-active {
  transform: translate(0);
}

.small__menu_list {
  list-style: none;
  padding: 0;
}

.small__menu_list-item {
  margin: 10px 15px;
  padding: 3px;
  border: 1px solid #eac02a;
}

@media only screen and (max-width: 768px) {
  .menu {
    display: none;
  }
  .small__menu {
    display: block;
  }
  .small__menu_body {
    display: block;
  }
}
</style>
