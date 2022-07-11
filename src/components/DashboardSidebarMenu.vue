<template >
  <div class="body">
    <div class="navigation" :class="{ 'active': active }">
      <ul>
        <li v-for="(item, index) in items" :key="index">
          <a href="#">
            <span class="icon">
              <ion-icon :name="item.iconName"></ion-icon>
            </span>
            <span class="title">{{ item.title }}</span></a>
        </li>
      </ul>
      <div class="toggle" @click="active = !active"></div>
    </div>
  </div>
</template>
<script setup lang="ts">
import { reactive, ref } from 'vue';

class list {
  title: string = '';
  iconName: string = '';
  constructor() { }
}

let items = reactive<list[]>([{
  iconName: 'logo-apple',
  title: 'Brand Name',
}, {
  iconName: 'home-outline',
  title: 'Dashboard',
}, {
  iconName: 'person-outline',
  title: 'Customers',
}, {
  iconName: 'chatbubble-outline',
  title: 'Messagers',
}, {
  iconName: 'help-outline',
  title: 'Help',
}, {
  iconName: 'settings-outline',
  title: 'setting',
}, {
  iconName: 'lock-closed-outline',
  title: 'password',
}, {
  iconName: 'log-out-outline',
  title: 'Sign Out',
},]);

let active = ref(false);

</script>

<style lang="scss" scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Poppins', sans-serif;
}

.body {
  min-height: 100vh;
  background: #365fa1;

  .navigation {
    position: fixed;
    inset: 20px;
    background: #287bff;
    width: 80px;
    border-left: 10px solid #287bff;
    border-radius: 50px;
    overflow: hidden;
    box-shadow: 15px 15px 25px rgba(0, 0, 0, 0.05);
    transition: .5s;

    ul {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;

      li {
        position: relative;
        list-style: none;
        width: 100%;
        border-top-left-radius: 30px;
        border-bottom-left-radius: 30px;

        &:hover {
          background: #fff;

          &:not(:first-child) a {
            color: #365fa1;
          }
        }

        &:nth-child(1) {
          top: 20px;
          margin-bottom: 40px;
          background: none;
        }

        &:not(:first-child):hover {

          &::before,
          &::after {
            content: '';
            position: absolute;
            right: 0;
            width: 20px;
            height: 20px;
            background: transparent;
          }

          &::before {
            top: -20px;
            border-bottom-right-radius: 20px;
            box-shadow: 7.5px 7.5px 0 7.5px #fff;
          }

          &::after {
            bottom: -20px;
            border-top-right-radius: 20px;
            box-shadow: 7.5px -7.5px 0 7.5px #fff;
          }
        }

        a {
          position: relative;
          display: block;
          width: 100%;
          display: flex;
          text-decoration: none;
          color: #fff;

          .icon {
            position: relative;
            display: block;
            min-width: 60px;
            height: 60px;
            line-height: 70px;
            text-align: center;

            ion-icon {
              font-size: 1.75em;
            }
          }

          .title {
            position: relative;
            display: block;
            padding: 0 10px;
            height: 60px;
            line-height: 60px;
            text-align: start;
            white-space: nowrap;
          }
        }
      }
    }

    .toggle {
      position: absolute;
      display: flex;
      justify-content: center;
      align-items: center;
      bottom: 15px;
      right: 15px;
      width: 50px;
      height: 50px;
      background: #fff;
      border-radius: 50%;
      box-shadow: 5px 5px 10px rgba(0, 0, 0, 0.15);
      cursor: pointer;

      &::before,
      &::after {
        content: '';
        position: absolute;
        width: 26px;
        height: 3px;
        border-radius: 3px;
        background: #365fa1;
        transition: 1s;
      }

      &::before {
        transform: translateY(-5px);
      }

      &::after {
        transform: translateY(5px);
      }
    }

    &.active {
      width: 300px;
      border-radius: 20px;

      .toggle {
        &::before {
          transform: translateY(0px) rotate(-405deg);
        }

        &::after {
          transform: translateY(0px) rotate(225deg);
        }
      }
    }
  }
}
</style>