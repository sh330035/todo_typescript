<template>
  <div class="min-h-screen bg-slate-200 flex flex-col align-middle">
    <h3 class="font-serif text-2xl text-center my-6 underline">To Do List</h3>
    <div class="w-full flex justify-center">
      <input type="text" v-model="todoText" class="w-96 px-3 py-2 rounded-lg border-black" placeholder="your to do list...">
      <button 
      @click="addTodoList"
      class="mx-4 px-4 py-1 bg-[#60A5FA] bg-opacity-90 rounded-lg text-white active:bg-[#3B82F6]">Add</button>
    </div>
    <div class="w-full flex flex-col justify-between pt-14 place-items-center">
      <div 
      v-for="(item, index) in todoList"
      class="w-1/2 my-4 flex justify-between ">
        <p class="bg-orange-400 opacity-50">{{item.title}}</p>
        <div>
          <button class="mx-2 px-4 py-1 rounded-lg bg-[#A7F3D0]">Done</button>
          <button @click="deleteTodoList(index)" class="mx-2 px-4 py-1 rounded-lg bg-[#F9A8D4]">Delete</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'

interface TodoType {
  title: string,
  is_completed: boolean,
};

let todoList = ref<TodoType[]>([])

const todoText = ref<string>('');

// 排序
const todoListSort = (list: TodoType[]) => {
  let completedList:TodoType[] = [];
  let otherList:TodoType[] = [];

  list.forEach(item => {
    if(item.is_completed){
      completedList.push(item);
    }else{
      otherList.push(item);
    }
  })

  return[...otherList, ...completedList]

}

const addTodoList = () =>{
  // 若 todoText 為空，則直接結束
  if(!todoText.value) return
  
  // 添加至 todoList 最前項，須符合 todoType
  todoList.value.unshift({
    title: todoText.value,
    is_completed: false
  })

  todoText.value = ''

  todoList.value = todoListSort(todoList.value)
}

const deleteTodoList = (index: number) =>{
  todoList.value.splice(index, 1)
}

</script>