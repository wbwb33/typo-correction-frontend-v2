<template>
  <div class="formContainer">
    <div class="formContainer__section">
      <form class="formContainer__form" @submit.prevent="search">
        <input type="text" class="formContainer__input" v-model="keyword" @input="onChangeKeyword" />
        
        <p>Message is: {{ keyword }}</p>
      </form>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  data() {
    return {
      keyword: ''
    }
  },
  methods: {
    async onChangeKeyword() {
      if(this.keyword.slice(-1)==" ") {
        const ip = await this.$axios.$post('http://116.193.191.166:8000',{
          value: this.keyword
        })
        this.keyword = ip.result;
      }
    }
  }
})
</script>


<style>
.formContainer {
  width: 100%;
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
}
.formContainer__section {
  width: 40%;
  text-align: center;
}
.formContainer__section-img {
  margin-bottom: 12px;
}
.formContainer__input {
  width: calc(100% - 100px);
  border-radius: 24px;
  padding: 0 50px;
  height: 50px;
  border: 1px solid #dfe1ef;
  outline: none;
  font-size: 18px;
}
.formContainer__form {
  position: relative;
}
.searchIcon {
  position: absolute;
  left: 25px;
  top: 18px;
  color: #9aa0ab;
}
.microphone {
  position: absolute;
  right: 25px;
  top: 16px;
  color: #4285f4;
}
.btn-google {
  background: #f2f2f2;
  color: #5f6368;
  padding: 10px 16px;
  border: none;
  outline: none;
  border-radius: 3px;
  margin-top: 20px;
}
</style>