<template>
  <div>
    <div class="hamburger_btn" v-on:click='ActiveBtn=!ActiveBtn'>
      <span class="line line_01" v-bind:class="{'btn_line01':ActiveBtn}"></span>
      <span class="line line_02" v-bind:class="{'btn_line02':ActiveBtn}"></span>
      <span class="line line_03" v-bind:class="{'btn_line03':ActiveBtn}"></span>
    </div>
    <!--サイドバー-->
    <transition name="menu">
      <div class="menu" v-show="ActiveBtn">
        <!-- <transition-group name="list" tag="ul"> -->
          <ul>
          <li v-show="ActiveBtn"><a href="#">項目1</a></li>
          <li v-show="ActiveBtn"><a href="#">項目2</a></li>
          <li v-show="ActiveBtn"><a href="#">項目3</a></li>
          <li v-show="ActiveBtn"><a href="#">項目4</a></li>
          <li v-show="ActiveBtn"><a href="#">項目5</a></li>
          <li v-show="ActiveBtn"><a href="#">項目6</a></li>
          </ul>
        <!-- </transition-group> -->
      </div>
  </transition>
  </div>
</template>

<script>
export default {
  data() {
    return {
      ActiveBtn: false
    }
  }
}
</script>

<style>
/*ボタン*/
.hamburger_btn {
  position: fixed; /*常に最上部に表示したいので固定*/
  top: 0;
  right: 0;
  width: 70px;
  height: 72px;
  cursor: pointer;
  z-index: 50;
}

.hamburger_btn .line {
  position: absolute;
  top: 0;
  left: 20px;
  width: 32px;
  height: 2px;
  background: #333333;
  text-align: center;
}

.hamburger_btn .line_01 {
  top: 16px;
  transition: 0.4s ease;
}
.hamburger_btn .line_02 {
  top: 26px;
  transition: 0.4s ease;
}
.hamburger_btn .line_03 {
  top: 36px;
  transition: 0.4s ease;
}


.btn_line01 {
  transform: translateY(10px) rotate(-45deg);
  transition: 0.4s ease;
}
.btn_line02 {
  transition: 0.4s ease;
  opacity: 0;
}
.btn_line03 {
  transform: translateY(-10px) rotate(45deg);
  transition: 0.4s ease;
}

/*サイドバー*/
.menu-enter-active, .menu-leave-active {
  transition: width 0.5s;
}
.menu-enter, .menu-leave-to {
  width: 0rem!important;
}
.menu-leave, .menu-enter-to{
  width: 20rem !important
}

.menu-enter-active li, .menu-leave-active li {
  transition: opacity 0.5s;
  transition-delay: 0.2s;
}
.menu-enter li, .menu-leave-to li {
  opacity: 0 !important;
}
.menu-leave li, .menu-enter-to li {
  opacity: 1 !important
}

.menu li {
  list-style: none;
  line-height: 1;
  padding: 1rem;
  opacity: 1;
}

.menu {
  background-color: rgba(197, 197, 197, 0.671);
  z-index: 30;
  position: fixed;
  width: 20rem;
  height: 80rem;
  top: 0;
  right: 0;
}
.menu a {
  color: rgb(66, 66, 66);
  text-decoration: none;
  font-size: 1.2rem;
  padding: 0 2rem;
}
.menu ul{
  margin: 1rem;
  padding: 0;
}
</style>
