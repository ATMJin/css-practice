<template>
  <div class="body">
    <div class="navigation">
      <ul>
        <li v-for="(list, index) in lists" :key="index" :class="['list', { 'active': list.active }]"
          @mouseover="activeLine(index)">
          <a href="#">
            <span class="icon">
              <ion-icon :name="list.iconName"></ion-icon>
            </span>
            <span class="text">{{ list.text }}</span>
          </a>
        </li>
        <div class="indicator"></div>
      </ul>
    </div>
  </div>
</template>

<script lang="ts" setup>
import { reactive } from 'vue';
class list {
  text: string = '';
  iconName: string = '';
  active: boolean = false;
  constructor() { }
}
let lists = reactive<list[]>([
  {
    text: 'Home',
    iconName: 'home-outline',
    active: true,
  }, {
    text: 'Profile',
    iconName: 'person-outline',
    active: false,
  }, {
    text: 'Message',
    iconName: 'chatbubble-outline',
    active: false,
  }, {
    text: 'Photos',
    iconName: 'camera-outline',
    active: false,
  }, {
    text: 'Settings',
    iconName: 'settings-outline',
    active: false,
  }]);

let activeLine = (i: number) => {
  lists.forEach((el) => { el.active = false; });
  lists[i].active = true;
};
</script>

<style lang="scss" scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Poppins', sans-serif;
}

$clr: #222327;

.body {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  background: $clr;
}

.navigation {
  position: relative;
  width: 400px;
  height: 70px;
  background: #fff;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 10px;

  ul {
    display: flex;
    width: 350px;

    li {
      position: relative;
      list-style: none;
      width: 70px;
      height: 70px;
      z-index: 1;

      a {
        position: relative;
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
        width: 100%;
        text-align: center;
        font-weight: 500;

        .icon {
          position: relative;
          display: block;
          line-height: 75px;
          font-size: 1.5em;
          text-align: center;
          transition: .5s;
          color: $clr;
        }

        .text {
          position: absolute;
          color: $clr;
          font-weight: 400;
          font-size: 0.75em;
          letter-spacing: 0.05em;
          transition: .5s;
          transform: translateY(20px);
        }
      }

      &.active {
        .icon {
          transform: translateY(-35px);
        }

        .text {
          opacity: 1;
          transform: translateY(10px);
        }
      }

      @for $i from 1 through 5 {
        &:nth-child(#{$i}).active~.indicator {
          transform: translateX(calc(70px * (#{$i} - 1)));
        }
      }
    }
  }
}

.indicator {
  position: absolute;
  top: -50%;
  width: 70px;
  height: 70px;
  background: #29fd53;
  border-radius: 50%;
  border: 6px solid $clr;
  transition: .5s;

  &::before,
  &::after {
    content: '';
    position: absolute;
    top: 50%;
    width: 20px;
    height: 20px;
    background: transparent;
  }

  &::before {
    left: -22px;
    border-top-right-radius: 20px;
    box-shadow: 1px -10px 0 0 $clr;
  }

  &::after {
    right: -22px;
    border-top-left-radius: 20px;
    box-shadow: -1px -10px 0 0 $clr;
  }
}
</style>