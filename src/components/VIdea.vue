<script setup>
//Выберите время, предмет и класс. <br> Ученики получат уведомление о <br> предстоящем уроке.
const idea = [
  {
    img: {
      src: "/Timetable.png",
      alt: "Timetable"
    },
    h3: "Составьте расписание",
    text: [{message: "Выберите время, предмет и класс."}, {message: "Ученики получат уведомление"} , {message: "о предстоящем уроке."}]
  },
  {
    img: {
      src: "/Group.png",
      alt: "Group"
    },
    h3: "Подготовьте материал",
    text: [{message: "Загружайте необходимые материалы "}, {message: " к уроку"}]
  },
  {
    img: {
      src: "/Lesson.png",
      alt: "Lesson"
    },
    h3: "Начните урок с учениками",
    text: [ {message: "Задавайте вопросы и вызывайте "} , {message:" «к доске» детей с поднятой рукой."}]
  },

]
</script>

<template>
  <section class="idea" id="idea">
    <div class="container">
      <h2>
        Как это работает?
      </h2>
      <div class="row">
        <div class="col-sm-4"
             v-for="(item,index) in idea"
             :key="index">
          <div class="idea__Card">
            <div class="idea__Card-img-wrap">
              <img :src="item.img.src" :alt="item.img.alt">
            </div>
            <div class="idea__Card-h3">
              {{ item.h3 }}
            </div>
            <div class="idea__Card-text">
              <div v-for="text in item.text">
                {{ text.message }}
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>

</style>