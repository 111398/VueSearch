<template>
  <div id="App" class="input-group mb-3 w-50">

    <!-- Вариант инпута с крестиком рабочий, стили для него внизу закомичены -->
    <!-- <input type="search" v-model="search" class="search" :placeholder="`${this.spec}`"> 
    <ul>
      <li v-for="item in searchHandler" :key="item.id">
        <p>Врач: <strong>{{item.title}}</strong></p>
      </li>
    </ul> -->
    <input name="doctors" class="form-control" list="doctors" :placeholder="`${this.spec}`"/>
    <datalist class="datalist" id="doctors">
      <option :value="`${item.title}`" v-for="item in searchHandler" :key="item.id"></option>
    </datalist>
    <button class="btn btn-primary" type="button" id="button-addon2">Найти</button>
  </div> 


</template>
<script>
import {doctors} from './data.js'

export default {
  data() {
    return {
      search: '',
      data: [],
      spec: 'Специализация',
    }
  },
  created() {
    this.data = doctors
    console.log(this.data);
  },
  computed: {
    searchHandler() {
      return this.data.filter((el) => {
        return el.title.toLowerCase().includes(this.search.toLowerCase())
      })
    },
    } 
}
</script>
<style scoped>
/* * {
  margin: 0;
  padding: 0;
  }
#App{
  justify-content: center;
  flex-direction: column;
} */
</style>
