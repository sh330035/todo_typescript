<template>
  <div class="min-h-screen bg-slate-200 flex flex-col align-middle">
    <h3 class="font-serif text-2xl text-center my-6 underline">To Do List</h3>
    <div class="w-full flex justify-center">
      <input type="text" class="w-96 px-3 py-2 rounded-lg border-black" placeholder="your to do list...">
      <button class="mx-4 px-4 py-1 bg-[#60A5FA] bg-opacity-90 rounded-lg text-white active:bg-[#3B82F6]">Add</button>
    </div>
    <div class="w-full flex justify-center pt-16">
      <div class="w-7/12 flex justify-between">
        <p class="bg-orange-400 opacity-50">somthing tedfg</p>
        <div>
          <button class="mx-2 px-4 py-1 rounded-lg bg-[#A7F3D0]">Done</button>
          <button class="mx-2 px-4 py-1 rounded-lg bg-[#F9A8D4]">Delete</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">

</script>