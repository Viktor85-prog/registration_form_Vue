<template>
  <div class="container m-5 mx-auto">

    <h6 class="mb-4">Информация об организаторе</h6>
    <form>
      <div class="mb-3">
        <label for="organization" class="form-label">Организатор</label>
        <input type="text" class="form-control" id="organization" placeholder="Coca-Cola">
      </div>

      <h6 >Контактные данные</h6> 
      <div class="row g-3 mb-4 mt-2">
        <div class="col-md">
          <label for="exampleInputEmail1" class="form-label">Телефон</label>
          <input type="phone" class="form-control" id="phone" placeholder="+7 (999) 555-33-22">
        </div>
        <div class="col-md">
          <label for="exampleInputEmail1" class="form-label">E-mail</label>
          <input type="email" class="form-control" id="email" placeholder="ivanov@mail.ru">
        </div>
        <div class="col-md">
          <label for="exampleInputEmail1" class="form-label">Город организатора</label>
          <input type="text" class="form-control" id="city" placeholder="Казань">
        </div>
      </div>

      <h6 class="mb-4">Общая информация</h6>
      <div class="mb-4">
        <label for="name" class="form-label">Название</label>
        <input type="text" class="form-control" id="name">
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
        <label for="detailed_description" class="form-label">Подробное описание</label>
        <textarea class="form-control" id="detailed_description" rows="3"></textarea>
      </div>

      <div class="row g-4 mb-5 mt-2 meeting">
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

      <div class="row g-4 mb-5 mt-2 meeting">
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
          <label for="age" class="form-label">Рейтинг мероприятия</label>
          <select class="form-select" id="age">
            <option value="18" selected>18+</option>
            <option value="0">0+</option>
            <option value="3">3+</option>
            <option value="60">60+</option>
          </select>
        </div>
        <div class="col-md">
          <label for="address" class="form-label">Адрес мероприятия</label>
          <input type="text" class="form-control" id="address">
        </div>
      </div>
      <button type="button" class="btn_custom">Отменить</button>
      <button type="button" class="btn_custom">Далее</button>
    </form>
  </div>
</template>

<script>

export default {

}
</script>

<style>

</style>
