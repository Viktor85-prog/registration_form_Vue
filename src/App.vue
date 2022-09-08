<template>
  <div class="container m-5 mx-auto">

    <div v-show="page === 1" class="page">
      <h6 class="mb-4">Информация об организаторе</h6>
      <form>
        <div class="mb-3">
          <label for="organization" class="form-label">Организатор</label>
          <input type="text" v-model="formReg.organization" class="form-control" id="organization" placeholder="Coca-Cola">
        </div>
        <h6 >Контактные данные</h6>
        <div class="row g-3 mb-4 mt-2">
          <div class="col-md">
            <label for="phone" class="form-label">Телефон</label>
            <input type="phone" v-model="formReg.phone" class="form-control" id="phone" placeholder="+7 (999) 555-33-22">
          </div>
          <div class="col-md">
            <label for="email" class="form-label">E-mail</label>
            <input type="email" v-model="formReg.email" class="form-control" id="email" placeholder="ivanov@mail.ru">
          </div>
          <div class="col-md">
            <label for="city" class="form-label">Город организатора</label>
            <input type="text" v-model="formReg.city"  class="form-control" id="city" placeholder="Казань">
          </div>
        </div>
        <h6 class="mb-4">Общая информация</h6>
        <div class="mb-4">
          <label for="name" class="form-label">Название</label>
          <input type="text"  v-model="formReg.name" class="form-control" id="name">
        </div>
        <h6 class="mb-4">Фотография</h6>
        <div class="d-flex flex-row mb-3">
          <div class="card_custom">
            <img src="../src/assets/addPhoto.jpg" class="card-img-top card_img" alt="...">
            <div class="card-body">
              <p class="card-text">Главная фотография (обложка мероприятия)</p>
            </div>
          </div>
            <div class="card_custom">
            <img src="../src/assets/tea.jpg" class="card-img-top card_img" alt="...">
            <div class="card-body">
              <p class="card-text">Главная фотография (обложка мероприятия)</p>
            </div>
          </div>
        </div>
        <div class="mb-3">
          <label for="description" class="form-label">Подробное описание</label>
          <textarea class="form-control" id="description" rows="3"  v-model="formReg.description"/>
        </div>
        <div class="row g-4 mb-5 mt-2 meeting">
          <div class="col-md">
            <label for="start_date1" class="form-label">Дата начала</label>
            <input type="date" class="form-control"  v-model="formReg.start_date1" id="start_date1" value="22.12.2019">
          </div>
          <div class="col-md">
            <label for="start_time1" class="form-label">Время начала</label>
            <input type="time" class="form-control" v-model="formReg.start_time1" id="start_time1" >
          </div>
          <div class="col-md">
            <label for="end_date1" class="form-label">Дата окончания</label>
            <input type="date" class="form-control" v-model="formReg.end_date1"  id="end_date1" >
          </div>
          <div class="col-md">
            <label for="end_time1" class="form-label">Время окончания</label>
            <input type="time" class="form-control"  v-model="formReg.end_time1" id="end_time1" >
          </div>
        </div>
        <div class="row g-4 mb-5 mt-2 meeting">
          <div class="col-md">
            <label for="start_date2" class="form-label">Дата начала</label>
            <input type="date" class="form-control" id="start_date2" value="22.12.2019">
          </div>
          <div class="col-md">
            <label for="start_time2" class="form-label">Время начала</label>
            <input type="time" class="form-control" id="start_time2" >
          </div>
          <div class="col-md">
            <label for="end_date2" class="form-label">Дата окончания</label>
            <input type="date" class="form-control" id="end_date2" >
          </div>
          <div class="col-md">
            <label for="end_time2" class="form-label">Время окончания</label>
            <input type="time" class="form-control" id="end_time2" >
          </div>
        </div>
        <div class="row g-4 mb-4 meeting_new">
          <div class="col-md">
            <label for="start_date" class="form-label">Дата начала</label>
            <input type="date" class="form-control" id="start_date" value="22.12.2019">
          </div>
          <div class="col-md">
            <label for="start_time" class="form-label">Время начала</label>
            <input type="time" class="form-control" id="start_time" >
          </div>
          <div class="col-md">
            <label for="end_date" class="form-label">Дата окончания</label>
            <input type="date" class="form-control" id="end_date" >
          </div>
          <div class="col-md">
            <label for="end_time" class="form-label">Время окончания</label>
            <input type="time" class="form-control" id="end_time" >
          </div>
        </div>
        <button type="button" class="btn_custom btn_custom__small ">+ Добавить дату</button>
        <div class="row g-2 mb-4 mt-5">
          <div class="col-md mb-3">
            <label for="rating" class="form-label">Рейтинг мероприятия</label>
            <select class="form-select" id="rating"  v-model="formReg.rating">
              <option value="18" selected>18+</option>
              <option value="0">0+</option>
              <option value="3">3+</option>
              <option value="60">60+</option>
            </select>
          </div>
          <div class="col-md">
            <label for="address" class="form-label">Адрес мероприятия</label>
            <input type="text" class="form-control" id="address"  v-model="formReg.address">
          </div>
        </div>
        <button type="button" class="btn_custom">Отменить</button>
        <button @click="nextPage" type="button" class="btn_custom">Далее</button>
      </form>
    </div>

    <div v-show="page === 2" class="page">
      <div class="info mb-5">
        <img src="../src/assets/attention.jpg" alt="">
        <span class="ml-4">Проверьте ваше мероприятие на наличие ошибок, если все в порядке - отправляйте на модерацию</span>
      </div>

      <div class=" mb-3" style="max-width: 600px;">
        <div class="row g-0 d-flex justify-content-around">
          <div class="col-md-1 mt-2 rectangle">
            16+
          </div>
          <div class="col-md-8">
            <div class="card-body">
              <h3 class="card-title mb-4">Чайный заголовок — писать не длиннее трёх строк</h3>
              <p class="card_text_custom"> <img src="../src/assets/place_img.jpg" alt=""> г. Казань, ул. Волкова, д. 7/29</p>
              <p class="card_text_custom"><img src="../src/assets/date_img.jpg" alt="">21 окт. 2019 (пт), 21 окт. 2019 (пт)</p>
              <p class="card_text_custom"><img src="../src/assets/time_img.jpg" alt="">17:30, 16:30</p>
              <h6 class="mt-4 mb-2">Контакты</h6>
              <p class="card_text_custom"> <img src="../src/assets/phone_img.jpg" alt="">+7 (999) 888-77-66</p>
              <p class="card_text_custom"><img src="../src/assets/mail_img.jpg" alt="">example@mail.com</p>
            </div>
          </div>
          <div class="col-md-2">
            <img src="../src/assets/tea_big.jpg" class=" rounded-end" alt="...">
          </div>
        </div>
      </div>
    <div class="some_text mb-5">
      В лаборатории жгучих перцев соберём собственные аппараты для экстракции. Узнаем, чем на самом деле пахнет мята, почему красный перец такой жгучий и получим привычные 
      для кухни запахи лабораторным способом. В лаборатории вареных яиц c помощью физико-химических методов вычислим идеальное время для варки куриного яйца. Отделим желток 
      от белка, проведем качественное сравнение составов и узнаем все о стоимости выеденного яйца. В лаборатории консервированных ананасов познакомимся с тушенкой и разберемся 
      в методах сохранения продуктов. Законсервируем парочку ананасов четырьмя разными способами и заберем все это домой, чтобы выяснить, какой метод консервации лучше.
    </div>

      <button @click="prewPage" type="button" class="btn_custom">Назад</button>
      <button  type="button" class="btn_custom">Отправить на модерацию</button>
    </div>

  </div>
</template>

<script>

export default {
  data() {
    return {
      page:1,
      formReg: {
        organization:'',
        phone:'',
        email:'',
        city:'',
        name:'',
        photo:'',
        description:'',
        start_date1:'',
        start_time1:'',
        end_date1:'',
        end_time1:'',
        rating:'',
        address:''
      }
    }
  },
  methods: {
    nextPage() {
      this.page++
    },
    prewPage() {
      this.page--
    }
  }
}
</script>

<style>

</style>
