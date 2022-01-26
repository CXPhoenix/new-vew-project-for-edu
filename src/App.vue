<script>
import { ref } from "vue"
export default {
    setup() {
        const datas = ref([]);
        const message = ref('');

        const addData = function() {
            if (message.value == '') {
                return;
            }
            datas.value.push(message.value);
            message.value = '';
        }

        return {
            datas,
            message,
            addData
        }
    },
}
</script>


<template>
  <header class="p-10 bg-blue-200 mb-1">
    <h1 class="text-center text-[3rem] text-gray-800">TODO List</h1>
  </header>
  <section id="creater" class="mt-4 mb-1">
    <form class="text-center">
      <label class="w-10/12 block mx-auto space-y-2" for="todo-create">
          <h2 class="text-3xl tracking-[.35rem]">請填寫代辦事項：</h2>
          <input autocomplete="off" type="text" class="w-full border-2 border-gray-400 rounded-md px-2 py-1 text-xl" id="todo-create" v-model="message" />
          <input type="submit" value="提交" v-bind:disabled="message == ''" @click.prevent="addData"  class="py-3 w-full  bg-green-500 rounded-md text-center text-2xl text-gray-100 cursor-pointer hover:bg-green-700 active:translate-y-1 disabled:bg-gray-400">
      </label>
    </form>
  </section>
  <section id="reader" class="mt-12 mb-8 space-y-4">
    <div
      v-for="(data, index) in datas"
      :key="index"
      class="w-9/12 px-3 mx-auto flex justify-between items-center border-2 border-gray-300 rounded-md"
    >
      <h2 class="text-2xl">{{index+1}}.&nbsp;&nbsp;{{data}}</h2>
      <font-awesome-icon icon="times-circle" @click="datas.splice(index,1)" class="text-red-600/40 text-2xl cursor-pointer hover:text-red-600" />
    </div>
  </section>
  <footer class="uppercase text-center fixed bottom-0 inset-x-0 bg-gray-200/50">power by cxphoenix</footer>
</template>

<style></style>
