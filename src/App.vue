<template>
  <div>
    <form class="form" @submit.prevent>
      <h1 class="form_title">Генератор названий для вашего бизнеса</h1>

      <div class="form_group">
        <input v-model="input" class="form_input" placeholder=" " />
        <label class="form_label">Описание компании</label>
      </div>

      <center>
        <button class="form_button" @click="sendWords">Названия</button>
      </center>
    </form>

    <form class="form_exit">
      <h1 class="form_title_exit">Сгенерированные названия</h1>

      <div class="form_group_exit">
        <textarea class="form_textarea" :value="array.join('\n')" disabled>
        </textarea>
      </div>
    </form>
  </div>
</template>
<script>
import axios from 'axios';
export default {
  data() {
    return {
      input: '56565',
      array: [],
    };
  },
  methods: {
    async sendWords() {
      try {
        const response = await axios.get('http://localhost:5000/arr');
        const data = response.data;
        this.array = data;
      } catch (er) {
        console.log(er);
      }
    },
  },
  mounted() {
    //this.getNames();
  },
};
</script>

<style>
/* С„РѕСЂРјР° 1 */
body {
  background: url(./assets/fone.jpg);
  background-size: cover; /* РјР°СЃС€С‚Р°Р±РёСЂРѕРІР°РЅРёРµ РєР°СЂС‚РёРЅРєРё С„РѕРЅР° */
  font-family: 'Montserrat', sans-serif;
}

.form {
  margin-top: 15%;
  height: 280px;
  width: 30%;
  float: left;
  margin-left: 20%;
  padding: 32px;
  background-color: #fdfffd;
  border-radius: 20px 0 0 20px;
  box-shadow: 0 4px 16px #ccc;
}

.form_title {
  text-align: left;
  margin: 0 0 32px 0;
  font-weight: 600;
  font-size: 25px;
  color: #546b4e;
}

.form_group {
  position: relative;
  margin-bottom: 32px;
}

.form_label {
  position: absolute;
  top: 0;
  color: #8f99a1;
  transition: 0.3s;
  font-size: 15px;
}

.form_input {
  position: absolute;
  width: 100%;
  padding: 0 0 10px 0;
  border: none;
  border-bottom: 1px solid #8f99a1;
  background-color: transparent;
  outline: none;
  transition: 0.3s;
}

.form_input:focus {
  border-bottom: 1px solid #546b4e;
}
.form_button {
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  color: #fff;
  background-color: #546b4e;
  outline: none;
  cursor: pointer;
  transition: 0.3s;
  text-align: center;
  margin-top: 70px;
}

.form_button:focus,
.form_button:hover {
  background-color: #738a6d;
}

.form_input:focus ~ .form_label,
.form_input:not(:placeholder-shown) ~ .form_label {
  top: -18px;
  font-size: 12px;
  color: #546b4e;
}

/* С„РѕСЂРјР° 2 */
.form_exit {
  margin-top: 15%;
  height: 280px;
  width: 30%;
  float: right;
  margin-right: 20%;
  padding: 32px;
  background-color: #546b4e;
  opacity: 0.7;
  border-radius: 0 20px 20px 0;
  box-shadow: 0 4px 16px #ccc;
}

.form_title_exit {
  text-align: left;
  margin: 0 0 32px 0;
  font-weight: 600;
  font-size: 21px;
  color: #ffffff;
}

.form_group_exit {
  position: relative;
  margin-bottom: 32px;
}

.form_textarea {
  position: absolute;
  width: 100%;
  padding: 0 0 10px 0;
  border-bottom: 1px solid #8f99a1;
  background-color: #e9e9e0;
  outline: none;
  height: 150px; /* Р’С‹СЃРѕС‚Р° РїРѕР»СЏ РІ РїРёРєСЃРµР»Р°С… */
  resize: none; /* Р—Р°РїСЂРµС‰Р°РµРј РёР·РјРµРЅСЏС‚СЊ СЂР°Р·РјРµСЂ */
}
</style>
