<template>
  <div id="app">
    <h1>App vue</h1>
    <button type="button" name="button" @click="active = !active">open modal</button>
    <div class="DatePicker">
      <p>DatePicker</p>
      <DatePicker v-model="date"></DatePicker>
    </div>
    <modal v-if="active" @closeModal = "active = !active">
        <template #header>
          <h2>Modal component</h2>
        </template>
        <template #body>
            <p>Some text</p>
        </template>
        <template #footer>
          <button type="button" name="button">button component</button>
        </template>
    </modal>

    <stepper id="stepper" :steps="8">
      <template #step1>
        <h1>elso lepes</h1>
        <button type="button" name="button">hozzaad</button>
      </template>

      <template #step2>
        <h1>masodik lepes</h1>
        <button type="button" name="button">kivalaszt</button>
        <button type="button" name="button">hozzaad</button>
      </template>

      <template #step3>
        <h1>harmadik lepes</h1>
        <input type="text" name="" value="">
        <button type="button" name="button">hozzaad</button>
      </template>

      <template #step4>
        <h1>negyedik lepes</h1>
        <button type="button" name="button">hozzaad</button>
      </template>
    </stepper>
  </div>
</template>

<script>
import DatePicker from 'v-calendar/lib/components/date-picker.umd'
import modal from './components/modal.vue'
import stepper from './components/stepper.vue'
export default {
  name: 'App',
  data() {
    return{
      active: false,
      date: new Date(2018, 0, 25)
    }
  },
  components: {
    modal,
    DatePicker,
    stepper,
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;

}
#stepper{
  margin-left: auto;
  margin-right: auto;
}
.DatePicker{
  width: 300px;
  margin-left: auto;
  margin-right: auto;
}
</style>
