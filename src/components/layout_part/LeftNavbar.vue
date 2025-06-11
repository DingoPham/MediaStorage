<script setup>
import ToHome from '../layout_part/left_navbar/ToHome.vue'
import PopupForNavbar from '../icons/PopupForNavbar.vue'
import { ref } from 'vue';

const isOpen = ref(false)
const toggleNavbar = () => {
    isOpen.value = !isOpen.value
}
</script>

<template>
    <div :class="['sidebar', {closed: !isOpen}]">
        <div class="toggle-wrapper">
            <PopupForNavbar :isOpen = "isOpen" @toggle="toggleNavbar"/>        
        </div>
    
    <transition name="fade">
        <nav v-if="isOpen" class="nav-content">
            <ToHome />
        </nav>
    </transition>
    </div>
</template>

<style scoped>
.sidebar {
  height: 100vh;
  background-color: #1d1d1d;
  color: white;
  overflow: hidden;
  display: flex;
  flex-direction: column;
  transition: width 0.3s ease;
  width: 200px; /* default open */
}

.sidebar.closed {
  width: 40px; /* khi đóng vẫn giữ 40px */
}

/* Toggle button luôn ở trên */
.toggle-wrapper {
  display: flex;
  justify-content: center;
  padding: 10px 0;
}

/* Nội dung của nav */
.nav-content {
  padding: 10px 20px;
}

/* Transition mượt */
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.001s ease;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>