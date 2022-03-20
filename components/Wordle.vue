<template>
<div>
  <b-form-input v-model="text" placeholder="5文字の英単語を入力してください。"></b-form-input>
</div>
</template>

<script>
import AnswerList from '../assets/json/wordleAnswerList.json'
import InputList from '../assets/json/wordleInputList.json'
export default {
  data() {
    return {
      answerList: AnswerList.answer,
      inputList: InputList.input
    }
  }
}
</script>

<style>

</style>
