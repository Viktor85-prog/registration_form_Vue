<template>
  <div class="container m-5 mx-auto">

    <div v-show="page === 1" class="page">
      <h6 class="mb-4">Информация об организаторе</h6>
      <form novalidate>
        <div class="mb-3">
          <label for="organization" class="form-label" >Организатор</label>
          <input 
              @blur="$v.formReg.organization.$touch()"
              type="text" 
              v-model="formReg.organization" 
              class="form-control"
              :class="{'is-invalid':$v.formReg.organization.$error}" 
              id="organization" 
              placeholder="Coca-Cola">
              <div v-if="!$v.formReg.organization.required" class="invalid-feedback">
                {{validationMessageRequired}}
              </div>
              <div v-if="!$v.formReg.organization.minLength" class="invalid-feedback">
                {{validationMessageLength4}}
              </div>
        </div>
        <h6 >Контактные данные</h6>
        <div class="row g-3 mb-4 mt-2">
          <div class="col-md">
            <label for="phone" class="form-label">Телефон</label>
            <input 
                type="phone"
                v-model="formReg.phone" 
                class="form-control"
                id="phone" 
                @blur="$v.formReg.phone.$touch()"
                :class="{'is-invalid':$v.formReg.phone.$error}" 
                placeholder="+7 (999) 555-33-22">
              <div v-if="!$v.formReg.phone.required" class="invalid-feedback">
                {{validationMessageRequired}}
              </div>
              <div v-if="!$v.formReg.phone.numeric" class="invalid-feedback">
                {{validationMessageAlpha}}
              </div>
              <div v-if="!$v.formReg.phone.minLength" class="invalid-feedback">
                {{validationMessageLength11}}
              </div>
          </div>
          <div class="col-md">
            <label for="email" class="form-label">E-mail</label>
            <input 
                type="email" 
                v-model="formReg.email" 
                class="form-control" 
                id="email" 
                @blur="$v.formReg.email.$touch()"
                :class="{'is-invalid':$v.formReg.email.$error}" 
                placeholder="ivanov@mail.ru">
                <div v-if="!$v.formReg.email.required" class="invalid-feedback">
                  {{validationMessageRequired}}
                </div>
                <div v-if="!$v.formReg.email.email" class="invalid-feedback">
                  {{validationMessageEmail}}
                </div>
          </div>
          <div class="col-md">
            <label for="city" class="form-label">Город организатора</label>
            <input 
                type="text" 
                v-model="formReg.city"  
                class="form-control" 
                id="city" 
                @blur="$v.formReg.city.$touch()"
                :class="{'is-invalid':$v.formReg.city.$error}" 
                placeholder="Казань">
                <div v-if="!$v.formReg.city.required" class="invalid-feedback">
                  {{validationMessageRequired}}
                </div>
                <div v-if="!$v.formReg.city.alpha" class="invalid-feedback">
                  {{validationMessageAlpha}}
                </div>
          </div>
        </div>
        <h6 class="mb-4">Общая информация</h6>
        <div class="mb-4">
          <label for="name" class="form-label">Название</label>
          <input 
              type="text"  
              v-model="formReg.name" 
              class="form-control" 
              @blur="$v.formReg.name.$touch()"
              :class="{'is-invalid':$v.formReg.name.$error}" 
              id="name">
              <div v-if="!$v.formReg.name.required" class="invalid-feedback">
                {{validationMessageRequired}}
              </div>
              <div v-if="!$v.formReg.name.maxLength" class="invalid-feedback">
                {{validationMessageLength60}}
              </div>
        </div>
        
        <h6 class="">Фотография</h6>
        <div class="d-flex flex-row mb-1">
          <div  class="card_custom relative">
            <div class="imagePreviewWrapper " 
              :style="{ 'background-image': `url(${previewImage})` }" 
              @click="selectImage"> 
              <img v-if="!previewImage" src="../src/assets/addPhoto.jpg" class="card-img-top card_img" alt="...">
            </div>
            <input ref="fileInput"  class="card_input" type="file" accept="image/*" @input="pickFile">
            <div class="card-body">
              <p class="card-text">Главная фотография (обложка мероприятия)</p>
            </div>
          </div>
        </div>

        <div class="mb-3">
          <label for="description" class="form-label">Подробное описание</label>
          <textarea 
          class="form-control" 
          id="description" 
          rows="3"  
          v-model="formReg.description"/>
        </div>
        <ul>
          <li v-for="(date, index) in formReg.dates" :key="index">
            <div class="row g-4 mb-5 mt-2 meeting">
              <div class="col-md">
                <label for="start_date1" class="form-label">Дата начала</label>
                <input type="text" 
                class="form-control"  
                id="start_date1" 
                disabled
                :value="date.start_date">
              </div>
              <div class="col-md">
                <label for="start_time1" class="form-label">Время начала</label>
                <input type="text" 
                id="start_time1" 
                class="form-control" 
                disabled
                :value="date.start_time">
              </div>
              <div class="col-md">
                <label for="end_date1" class="form-label">Дата окончания</label>
                <input type="text" 
                class="form-control" 
                :value="date.end_date"
                disabled
                id="end_date1" >
              </div>
              <div class="col-md">
                <label for="end_time1" class="form-label">Время окончания</label>
                <input type="text" 
                class="form-control"  
                disabled
                :value="date.end_time"
                id="end_time1" >
              </div>
            </div>
          </li>
        </ul>
        <div class="row g-4 mb-4 meeting_new">
          <div class="col-md">
            <label for="start_date" class="form-label">Дата начала</label>
            <input 
            type="date" 
            class="form-control" 
            v-model="formReg.newDate.start_date"
            :max="formReg.newDate.end_date"
            id="start_date">
            <!-- @blur="$v.formReg.start_date.$touch()" -->
            <!-- :class="{'is-invalid':$v.formReg.start_date.$error}"  -->
            <!-- <div v-if="!$v.formReg.start_date.required" class="invalid-feedback">
                {{validationMessageRequired}}
              </div> -->
          </div>
          <div class="col-md">
            <label for="start_time" class="form-label">Время начала</label>
            <input 
            type="time" 
            class="form-control" 
            v-model="formReg.newDate.start_time"
            :max="formReg.newDate.end_time"
            id="start_time" >
          </div>
          <div class="col-md">
            <label for="end_date" class="form-label">Дата окончания</label>
            <input 
            type="date" 
            v-model="formReg.newDate.end_date"
            class="form-control" 
            :min="formReg.newDate.start_date"
            id="end_date" >
          </div>
          <div class="col-md">
            <label for="end_time" class="form-label">Время окончания</label>
            <input 
            type="time" 
            class="form-control" 
            v-model="formReg.newDate.end_time"
            :min="formReg.newDate.start_time"
            id="end_time" >
          </div>
        </div>
        <button 
        type="button" 
        class="btn_custom btn_custom__small "
        @click="addDate">
        + Добавить дату</button>
        <div class="row g-2 mb-4 mt-5">
          <div class="col-md mb-3">
            <label for="rating" class="form-label">Рейтинг мероприятия</label>
            <select 
            class="form-select" 
            id="rating" 
            @blur="$v.formReg.rating.$touch()" 
            :class="{'is-invalid':$v.formReg.rating.$error}" 
            v-model="formReg.rating">
              <option 
                v-for="rating in formReg.ratings" 
                :key="rating.id" 
                :value="rating.title">
                {{ rating.title }}
              </option>
            </select>
            <div v-if="!$v.formReg.rating.required" class="invalid-feedback">
                {{validationMessageRequired}}
              </div>
          </div>
          <div class="col-md">
            <label for="address" class="form-label">Адрес мероприятия</label>
            <input 
                type="text" 
                class="form-control" 
                id="address"  
                @blur="$v.formReg.address.$touch()"
                :class="{'is-invalid':$v.formReg.address.$error}" 
                v-model="formReg.address">
              <div v-if="!$v.formReg.address.required" class="invalid-feedback">
                {{validationMessageRequired}}
              </div>
          </div>
        </div>
        <button @click="cancel" type="button" class="btn_custom">Отменить</button>
        <!-- :disabled="disabledNextBitton"  -->
        <!-- @click="formValidationTouch" -->
        <button 
        @click="nextPage"
        type="button" 
        class="btn_custom">Далее</button>
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
            {{formReg.rating}}
          </div>
          <div class="col-md-8">
            <div class="card-body">
              <h3 class="card-title mb-4">{{formReg.name}}</h3>
              <p class="card_text_custom"> <img src="../src/assets/place_img.jpg" alt="">{{formReg.address}}</p>
              <p class="card_text_custom"><img src="../src/assets/date_img.jpg" alt="">{{formReg.start_date1}}-{{formReg.end_date1}}</p>
              <p class="card_text_custom"><img src="../src/assets/time_img.jpg" alt="">{{formReg.start_time1}}-{{formReg.end_time1}}</p>
              <h6 class="mt-4 mb-2">Контакты</h6>
              <p class="card_text_custom"> <img src="../src/assets/phone_img.jpg" alt="">{{formReg.phone}}</p>
              <p class="card_text_custom"><img src="../src/assets/mail_img.jpg" alt="">{{formReg.email}}</p>
            </div>
          </div>
          <div class="col-md-2">
            <img :src="previewImage" class=" rounded-end page2_image" alt="...">
          </div>
        </div>
      </div>
    <div class="some_text mb-5">
      {{formReg.description}}
      <!-- В лаборатории жгучих перцев соберём собственные аппараты для экстракции. Узнаем, чем на самом деле пахнет мята, почему красный перец такой жгучий и получим привычные 
      для кухни запахи лабораторным способом. В лаборатории вареных яиц c помощью физико-химических методов вычислим идеальное время для варки куриного яйца. Отделим желток 
      от белка, проведем качественное сравнение составов и узнаем все о стоимости выеденного яйца. В лаборатории консервированных ананасов познакомимся с тушенкой и разберемся 
      в методах сохранения продуктов. Законсервируем парочку ананасов четырьмя разными способами и заберем все это домой, чтобы выяснить, какой метод консервации лучше. -->
    </div>

      <button @click="prewPage" type="button" class="btn_custom">Назад</button>
      <button  type="button" class="btn_custom">Отправить на модерацию</button>
    </div>

  </div>
</template>
<script>
import { required, minLength, maxLength, between, email, numeric, alpha } from 'vuelidate/lib/validators'
const axios = require('axios').default;

export default {
  data() {
    return {
      page:1,
      validationMessageRequired: "Поле обязательное для заполнения",
      validationMessageLength4:"Длинна должна быть не менее 4х символов",
      validationMessageLength11:"Длинна должна быть не менее 11 символов",
      validationMessageLength60:"Длинна должна быть не более 60 символов",
      validationMessageAlpha: "Поле должно состоять только из букв",
      validationMessageEmail: "Не кореектный адрес электронной почты",
      imgSrc: "/addPhoto.jpg",
      img:null,
      previewImage: null,
      formReg: {
        organization:'',
        phone:'',
        email:'',
        city:'',
        name:'',
        photo:'',
        description:'',
        newDate:  { 
            start_date:'',
            start_time:'',
            end_date:'',
            end_time:''
          },
        rating:'',
        address:'',
        dates:[
          { 
            start_date:'22.12.2019',
            start_time:'10:00',
            end_date:'22.12.2019',
            end_time:'12:00'
          },
          { 
            start_date:'22.12.2019',
            start_time:'10:00',
            end_date:'22.12.2019',
            end_time:'12:00'
          }
        ],
        ratings:[]
      }
    }
  },
  mounted() {
    axios
    .get('http://testwork.rdbx24.ru/api')
    .then(response => this.formReg.ratings = response.data.result)
    .catch(error => {
      console.log(error)
    })
  },
  computed: {    
    formValidation() {
          return  this.$v.formReg.organization.$invalid ||
                  this.$v.formReg.phone.$invalid ||
                  this.$v.formReg.email.$invalid ||
                  this.$v.formReg.city.$invalid ||
                  this.$v.formReg.name.$invalid  ||
                  this.$v.formReg.rating.$invalid ||
                  this.$v.formReg.address.$invalid
    }
  },
  methods: {
    selectImage () {
          this.$refs.fileInput.click()
      },
      pickFile () {
        let input = this.$refs.fileInput
        let file = input.files
        if (file && file[0]) {
          let reader = new FileReader
          reader.onload = e => {
            this.previewImage = e.target.result
          }
          reader.readAsDataURL(file[0])
          this.$emit('input', file[0])
        }
      },
    browseImg() {
      this.$refs.file.click()
    },
    changeImg(e) {
      this.img = e.target.files[0]
      this.$emit('input', this.img)

      let reader = new FileReader()
      reader.readAsDataURL(this.img)
      reader.onload = (e) => {
        this.imgSrc = e.target.result
      }
    },
    //  onChange(e) {
    //   const file = e.target.files[0]
    //   this.image = file
    //   this.img.imageUrl = URL.createObjectURL(file)
    // },
    addDate() {
      let dateObj = { 
            start_date:this.formReg.newDate.start_date,
            start_time:this.formReg.newDate.start_time,
            end_date:this.formReg.newDate.end_date,
            end_time:this.formReg.newDate.end_time
          }
      this.formReg.dates.push(dateObj)
      this.formReg.newDate =  { 
            start_date:'',
            start_time:'',
            end_date:'',
            end_time:''
          }
    },
    nextPage() {
      this.page++
    },
    prewPage() {
      this.page--
    },
    cancel() {
      for (let input in this.formReg) {
        this.formReg[input] = ''
      }
      this.$v.$reset()
    },
    formValidationTouch() {
        if (this.$v.formReg.organization.$invalid ||
              this.$v.formReg.phone.$invalid ||
              this.$v.formReg.email.$invalid ||
              this.$v.formReg.city.$invalid ||
              this.$v.formReg.name.$invalid  ||
              this.$v.formReg.rating.$invalid ||
              this.$v.formReg.address.$invalid) {
                this.$v.formReg.organization.$touch()
                this.$v.formReg.phone.$touch()
                this.$v.formReg.email.$touch()
                this.$v.formReg.city.$touch()
                this.$v.formReg.name.$touch()
                this.$v.formReg.rating.$touch()
                this.$v.formReg.address.$touch() 
        } else {
          this.nextPage()
        }
    }
    
  },
  validations: {
      formReg:{
        organization: {
          required,
          minLength: minLength(4)
        },
        phone:{
          required,
          numeric,
          minLength: minLength(10)
        },
        email:{
          required,
          email
        },
        city:{
          required,
          alpha
        },
        name:{
          required,
          maxLength: maxLength(60)
        },
        // photo:'',
        // description:'',
        start_date:{
          required
        },
        start_time:{
          required
        },
        end_date:{
          required
        },
        end_time:{
          required
        },
        rating:{
          required
        },
        address:{
          required
        },
        age: {
          between: between(20, 30)
        }
      }
  }
}
</script>

<style>

</style>
