<template>
  <div class="container">
    <form action="" class="card" @submit.prevent="submitHandler">
      <h1>Анкета на Vue разработчика</h1>
      <!-- <div class="form-control" :class="{invalid: errors.name}">
        <label for="name">Как тебя зовут?</label><br>
        <input 
        type="text" 
        id="name"
        placeholder="Введи имя"
        v-model.trim="name">
        <small v-if="errors.name">{{errors.name}}</small>
      </div> -->
      <app-input
        :placeholder="'Введи имя'"
        :error="errors.name"
        label="Как тебя зовут?"
        v-model="name"
      ></app-input>

      <div class="form-control">
        <label for="age">Выбери Возраст</label><br>
        <input 
        type="number" 
        id="age" 
        max="70"
        v-model.number="age"
        >
      </div>

      <div class="form-control">
        <label for="city">Твой город</label><br>
        <select id="city" v-model="city">
          <option value="ast">Astana</option>
          <option value="shy">Shymkent</option>
          <option value="ala">Almaty</option>
          <option value="Krg">Karaganda</option>
        </select>
      </div>

      <div class="form-checkbox">
        <span><div class="label">Готов к переезду в Токио?</div></span>
        <div class="checkbox">
          <label><input type="radio" name="trip" v-model="relocate" value="Yes">Да</label>
        </div>
        <div class="checkbox">
          <label><input type="radio" name="trip" v-model="relocate" value="No">Нет</label>
        </div>
      </div>
      <div class="form-checkbox">
        <span><div class="label">Что знаешь во Vue?</div></span>
        <div class="checkbox">
          <label><input type="checkbox" v-model="skills" value="vuex">Vuex</label>
        </div>
        <div class="checkbox">
          <label><input type="checkbox" v-model="skills" value="CLI">Vue CLI</label>
        </div>
        <div class="checkbox">
          <label><input type="checkbox" v-model="skills" value="Router">Vue Router</label>
        </div>
      </div>
      <button type="submit" class="btn primary">Отправить</button>
    </form>
  </div>
</template>

<script>
import AppInput from './AppInput.vue'
export default {
  data () {
    return {
      name: '',
      age: 23,
      city: 'shy',
      relocate: null,
      skills: [],
      errors: {
        name: null
      }
    }
  },

  components: { AppInput },

  methods: {
    formIsValid () {
      let isValid = true
      if (this.name.length === 0) {
        this.errors.name = 'Name cant be null'
        isValid = false
      } else {
        this.errors.name = null
      }
      return isValid
    },
    submitHandler () {
      if (this.formIsValid()) {
        console.group('Form Data')
        console.log('Name:', this.name)
        console.log('Age:', this.age)
        console.log('City:', this.city)
        console.log('Relocate:', this.relocate)
        console.log('Skills:', this.skills)
        console.groupEnd()
      }
    }
  }
}
</script>

<style>
  .form-control small{
    color:red;
  }
  .form-control.invalid input{
    border-color:red;
  }

  /* Основные стили */
body {
    margin: 0;
    padding: 0;
    font-family: Arial, Helvetica, sans-serif;
    background-color: #f0f4f8;
    color: #333;
  }
  
  /* Заголовки */
  h1, h2, h3, h4, h5, h6 {
    margin: 0;
    padding: 10px 0;
    color: #2c3e50;
  }
  
  /* Ссылки */
  a {
    color: #3498db;
    text-decoration: none;
  }
  
  a:hover {
    text-decoration: underline;
  }
  
  /* Контейнер */
  .container {
    width: 90%;
    max-width: 600px;
    margin: 50px auto;
    padding: 20px;
  }
  
  /* Кнопки */
  button {
    padding: 10px 15px;
    border: none;
    background-color: #3498db;
    color: white;
    cursor: pointer;
    border-radius: 5px;
    transition: background-color 0.3s;
  }
  
  button:hover {
    background-color: #2980b9;
  }
  
  /* Списки */
  ul {
    list-style-type: none;
    padding: 0;
  }
  
  ul li {
    margin: 5px 0;
  }
  
  /* Карточки */
  .card {
    background: white;
    padding: 30px;
    border-radius: 12px;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
    margin-bottom: 20px;
  }
  
  .card h1 {
    font-size: 1.8rem;
    color: #2c3e50;
    text-align: center;
    margin-bottom: 20px;
  }
  
  /* Формы */
  .form-control {
    margin-bottom: 20px;
  }
  
  label {
    font-size: 1rem;
    font-weight: bold;
    color: #2c3e50;
    margin-bottom: 5px;
    display: block;
  }
  
  input[type="text"],
  input[type="number"],
  select {
    width: 100%;
    padding: 12px 15px;
    font-size: 1rem;
    border: 1px solid #dcdcdc;
    border-radius: 8px;
    box-sizing: border-box;
    margin-top: 8px;
    transition: border-color 0.3s;
  }
  
  input[type="text"]:focus,
  input[type="number"]:focus,
  select:focus {
    border-color: #3498db;
    outline: none;
    box-shadow: 0 0 5px rgba(52, 152, 219, 0.5);
  }

/* Контейнер для группы чекбоксов/радиокнопок */
.form-checkbox {
    margin-bottom: 20px;
    background-color: #fff;
    padding: 15px;
    border-radius: 10px;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  }
  
  /* Заголовок группы */
  .form-checkbox .label {
    font-size: 1.1rem;
    font-weight: bold;
    color: #2c3e50;
    margin-bottom: 10px;
    display: block;
  }
  
  /* Контейнер для каждого элемента (чекбокс/радиокнопка) */
  .checkbox {
    margin: 8px 0;
    display: flex;
    align-items: center;
  }
  
  /* Стили для чекбоксов и радиокнопок */
  .checkbox input[type="checkbox"],
  .checkbox input[type="radio"] {
    margin-right: 10px;
    width: 18px;
    height: 18px;
    border: 1px solid #dcdcdc;
    border-radius: 4px;
    appearance: none; /* Убираем стандартное оформление */
    outline: none;
    cursor: pointer;
    transition: background-color 0.3s, border-color 0.3s;
  }
  
  /* Цвет фона и границы при наведении */
  .checkbox input[type="checkbox"]:hover,
  .checkbox input[type="radio"]:hover {
    border-color: #3498db;
  }
  
  /* Стили при выборе чекбокса/радиокнопки */
  .checkbox input[type="checkbox"]:checked,
  .checkbox input[type="radio"]:checked {
    background-color: #3498db;
    border-color: #3498db;
    position: relative;
  }
  
  /* Иконка галочки для чекбокса */
  .checkbox input[type="checkbox"]:checked::after {
    content: '✔';
    font-size: 12px;
    color: white;
    position: absolute;
    left: 4px;
    top: 0;
  }
  
  /* Метки (label) рядом с чекбоксами и радиокнопками */
  .checkbox label {
    font-size: 1rem;
    color: #333;
    cursor: pointer;
    display: flex;
    align-items: center;
  }
  
  /* Таблицы */
  table {
    width: 100%;
    border-collapse: collapse;
    margin: 20px 0;
  }
  
  table th,
  table td {
    padding: 10px;
    border: 1px solid #ddd;
    text-align: left;
  }
  
  table th {
    background-color: #3498db;
    color: white;
  }
  
  table tr:nth-child(even) {
    background-color: #f9f9f9;
  }
  
  /* Мобильные устройства */
  @media (max-width: 768px) {
    .container {
      width: 100%;
      padding: 10px;
    }
  
    h1 {
      font-size: 1.5rem;
    }
  }
  
</style>
