<script setup>
import {ref, watch} from 'vue';

const sidebarOpen = ref(false);
let scrollPosition = 0;

const toggleSidebar = () => {
  sidebarOpen.value = !sidebarOpen.value;
};

watch(sidebarOpen, (newValue) => {
  // Если newValue истинно, то aside открыт
  if (newValue) {
    // Сохраняем текущую позицию прокрутки
    scrollPosition = window.pageYOffset;
    // Устанавливаем стиль body так, чтобы прокрутка была заблокирована
    document.body.style.overflow = 'hidden';
    document.body.style.position = 'fixed';
    document.body.style.top = `-${scrollPosition}px`;
    document.body.style.width = '100%';
  } else {
    // Если newValue ложно, то aside закрыт
    // Удаляем стили, которые мы установили ранее, чтобы разблокировать прокрутку
    document.body.style.removeProperty('overflow');
    document.body.style.removeProperty('position');
    document.body.style.removeProperty('top');
    document.body.style.removeProperty('width');
    // Возвращаем прокрутку на место, где она была до открытия aside
    window.scrollTo(0, scrollPosition);
  }
});
</script>


<template>
  <header>
  <nav class="navigation">
      <div class="container">
        <div class="navigation__wrapp">
          <img src="/logo.svg" alt="logo">
          <ul class="navigation__list">
            <li class="navigation__list-item">
              <a href="#possibilities" class="navigation__list-link"> Возможности </a>
            </li>
            <li class="navigation__list-item">
              <a href="#idea" class="navigation__list-link"> Как это работает? </a>
            </li>
          </ul>
          <div class="navigation__menu" @click="toggleSidebar">
            <img src="/menu.svg" alt="menu">
          </div>
        </div>
      </div>
    </nav>
    <aside class="aside" :class="{ 'sidebar-open': sidebarOpen }">
      <div class="aside__wrapp">
        <div class="aside__close" @click="toggleSidebar">
          <img src="/close.svg" alt="close">
        </div>
        <ul class="aside__list">
          <li class="aside__list-item">
            <a href="#possibilities" class="aside__list-link"> Возможности </a>
          </li>
          <li class="aside__list-item">
            <a href="#idea" class="aside__list-link"> Как это работает? </a>
          </li>
        </ul>
        <div class="aside__info">
          <p>
            г Сургут, ул Базовая, д. 34, офис 10
f             ОГРН 1238600001200
            ИНН 8602309464
          </p>
          <p class="aside__info-p">
            ООО Дотсолюшн © 2023
          </p>
        </div>
      </div>
    </aside>
  </header>
</template>

<style scoped>

</style>