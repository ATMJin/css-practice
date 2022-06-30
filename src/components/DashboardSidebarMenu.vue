<template >
  <div class="body">
    <div class="navigation">
      <ul>
        <li v-for="(item, index) in items" :key="index">
          <a href="#">
            <span class="icon"></span>
            <span class="title"></span></a>
        </li>
      </ul>
    </div>
  </div>
</template>
<script setup lang="ts">
import { reactive } from 'vue';
let items = reactive([{
  icon: '',
  title: 'Brand Name',
}, {
  icon: '',
  title: 'Dashboard',
}, {
  icon: '',
  title: 'Customers',
}, {
  icon: '',
  title: 'Messagers',
}, {
  icon: '',
  title: 'Help',
}, {
  icon: '',
  title: 'setting',
}, {
  icon: '',
  title: 'password',
}, {
  icon: '',
  title: 'Sign Out',
},]);

</script>

<style lang="scss">
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
    background: #000;
  }
}
</style>