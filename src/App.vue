<script setup>
import { ref } from 'vue';

const count = ref(0); // defualt value

const 증가 = () => {
  //count.value++;
  count.value = count.value + 1;
};

const 감소 = () => {
  //count.value--;
  count.value = count.value - 1;
};

const inputValue = ref('test');
console.log(inputValue.value);

const changeInputValue = () => {
  console.log(inputValue.value);
};
const handleChange = (event) => {
  console.log('handle change');
  console.log(event);
  const nextValue = event.target.value;
  inputValue.value = nextValue;
};

const todoList = ref([
  { text: 'vue', done: true },
  { text: 'react', done: false },
  { text: 'vercel', done: false },
]);
//const techStack = ['vue', 'stackblitz']
const handleClickValue = () => {
  todoList.value.push(inputValue.value);
  console.log(todoList.value);
};
const handleClickDelete = (index) => {
  console.log(`handle click delete : ${index}`);
  //todoList.value = todoList.value.splice(index + 1);
  todoList.value.splice(index, 1);
};
const handleCheck = () => {};
</script>

<template>
  <div style="display: none">
    <div>count : {{ count }}</div>

    <button @click="증가;">+</button>
    <button @click="감소;">-</button>
  </div>
  <div>
    <h1>TODO LIST</h1>

    <br />
    <p>{{ todoList }}</p>
    <input v-model="inputValue" />
    <!-- <br />
  <input :model="inputValue" /><br />
  <input :value="inputValue" @input="handleChange" /><br /> -->
    <button @click="handleClickValue">확인</button>
    <span style="display: none">(input text: {{ inputValue }})</span>

    <div class="todo-item" v-for="(item, index) in todoList">
      <input type="checkbox" v-model="item.done" @check="handleCheck" />
      <span :class="{ done: item.done }">{{ index }}. {{ item.text }}</span>
      <button @click="handleClickDelete(index)" v-index="key">삭제</button>
    </div>
  </div>
</template>

<style scoped>
h1 {
  color: red;
}
.todo-item {
  width: 100%;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  border: 1px solid gray;
  border-bottom: 0;
}
.todo-item::last-child {
  border-bottom: 1px;
}
.todo-item span.done {
  text-decoration: line-through;
}
</style>
