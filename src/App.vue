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
</style>
