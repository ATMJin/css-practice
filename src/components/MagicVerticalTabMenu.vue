<template >
  <div class="body" :style="{ 'background': bodyBGC }">
    <div class="navigation">
      <ul>
        <li v-for="(item, index) in menuList" :key="index" :class="['list', { 'active': item.active }]"
          @mouseover="toggleActive(index)" @mouseenter="changeBodyBGC(index)">
          <a href="#">
            <span class="icon">
              <font-awesome-icon :icon="['fa-solid', item.icon]" />
            </span>
            <span class="title">{{ item.title }}</span>
          </a>
        </li>
        <div class="indicator"></div>
      </ul>
    </div>
  </div>
</template>

<script setup lang="ts">
import { reactive, ref } from 'vue';
let menuList = reactive([
  { title: "Home", icon: "fa-house", active: true, color: "#f53b57" },
  { title: "Profile", icon: "fa-user", active: false, color: "#3c40c6" },
  { title: "Message", icon: "fa-message", active: false, color: "#05c46b" },
  { title: "Help", icon: "fa-circle-question", active: false, color: "#0fbcf9" },
  { title: "Settings", icon: "fa-gear", active: false, color: "#ffa801" }]);
let bodyBGC = ref('');

let toggleActive = (i: number) => {
  menuList.forEach((el) => { el.active = false; });
  menuList[i].active = true;
};
let changeBodyBGC = (i: number) => {
  bodyBGC.value = menuList[i].color;
};
</script>

<style lang="scss" scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Poppins', sans-serif;
}

.body {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  background: #f53b57;
  transition: .5s
}

.navigation {
  position: relative;
  width: 70px;
  height: 350px;
  background: #fff;
  border-radius: 35px;
  box-shadow: 0 15px 25px rgba(0, 0, 0, 0.1);

  ul {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    display: flex;
    flex-direction: column;

    li {
      position: relative;
      list-style: none;
      width: 70px;
      height: calc(350px / 5);
      z-index: 1;

      a {
        position: relative;
        display: flex;
        justify-content: center;
        align-items: center;
        width: 100%;
        text-align: center;
        color: #333;
        font-weight: 500;

        .icon {
          position: relative;
          display: block;
          line-height: 75px;
          text-align: center;

          svg {
            width: 24px;
            height: 24px;
          }
        }

        .title {
          position: absolute;
          top: 50%;
          left: 110px;
          background: #fff;
          transform: translateY(-50%);
          padding: 5px 10px;
          border-radius: 6px;
          transition: .5s;
          box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
          opacity: 0;
          visibility: hidden;

          &::before {
            content: '';
            position: absolute;
            width: 12px;
            height: 12px;
            background: #fff;
            left: -8px;
            top: 46%;
            transform: rotate(45deg) translateY(-50%);
            border-radius: 2px;
          }
        }
      }

      &:hover .title {
        opacity: 1;
        visibility: visible;
        transform: translateX(-25px) translateY(-50%);
      }

      &.active .icon {
        color: #fff;
      }

      ~.indicator {
        position: absolute;
        left: 0;
        width: 70px;
        height: 70px;
        transition: .5s;

        &::before {
          content: '';
          position: absolute;
          width: 50px;
          height: 50px;
          top: 50%;
          left: 50%;
          transform: translate(-50%, -50%);
          background: #333;
          border-radius: 50%;
          transition: .5s;
        }
      }

      $color: [#f53b57, #3c40c6, #05c46b, #0fbcf9, #ffa801];

      @for $i from 1 through 5 {
        &:nth-child(#{$i}).active~.indicator {
          transform: translateY(calc(70px * (#{$i} - 1)));

          &::before {
            background: nth($color, $i);
          }
        }
      }
    }


  }
}
</style>