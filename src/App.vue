<template>
  <div id="app">
    <h1>Monty Hall's problem</h1>
    <div class="form">
      <div v-if="!started">
        <label for="doorAmount">How many doors?</label>
        <input
          type="text"
          id="doorAmount"
          size="3"
          v-model.number="doorAmount"
            >
      </div>
      <div v-if="!started">
          <label for="selectedDoor">What's the winning door?</label>
          <input type="text" id="selectedDoor" size="3"
          v-model.number="selectedDoor">
      </div>
      <button v-if="!started" @click="started=true">Start</button>
      <button v-if="started" @click="started=false">Restart</button>
    </div>
    <div class="doors" v-if="started">
        <div v-for="i in doorAmount" :key="i">
            <Door :hasGift="i === selectedDoor" :number="i"/> 
        </div>
    </div>
  </div>
</template>

<script>
import Door from "./components/Door";
export default {
  name: "App",
  components: { Door },
  data() {
    return {
      started: false,
      doorAmount: 3,
      selectedDoor: null,
    };
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  font-family: "Montserrat", sans-serif;
}
body {
  color: #FFF;
  background-color: #000;
}
#app {
  display: flex;
  flex-direction: column;
  align-items: center;
}
#app h1 {
  border: 1px solid #000;
  background-color:#52057b;
  border: 1px solid #FFF;
  padding: 20px;
  border-radius: 16px;
  margin-bottom: 60px;
}
.form{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    margin-bottom: 40px;
}
.form, .form input, .form button{
    margin-bottom: 10px;
    font-size: 2rem;

}
.form button{
  background-color: #bc6ff1;
  padding: 16px 64px;
  border-radius: 16px;
  color:#FFF;
  text-transform: uppercase;
  outline: none;
  margin-top: 32px;
  margin-bottom: 32px;

}
.doors{
    align-self: stretch;
    display: flex;
    justify-content: space-around;

    flex-wrap: wrap;
}
input{
  margin-left: 12px;
  outline: none;
  text-align: end;
  border-radius: 16px;
  padding:  0 8px;
}
</style>