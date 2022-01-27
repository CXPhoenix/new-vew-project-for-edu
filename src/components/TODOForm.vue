<script>
import { ref } from "vue";
export default {
  props: ["addDataFunction"],
  setup(props) {
    const message = ref("");
    const addData = function() {
        props.addDataFunction(message.value);
        message.value = "";
    }
    return {
      message,
      addData
    };
  },
};
</script>

<template>
  <section id="creater" class="mt-4 mb-1">
    <form class="text-center">
      <label class="w-10/12 block mx-auto space-y-2" for="todo-create">
        <h2 class="text-3xl tracking-[.35rem]">請填寫代辦事項：</h2>
        <input
          autocomplete="off"
          type="text"
          class="w-full border-2 border-gray-400 rounded-md px-2 py-1 text-xl"
          id="todo-create"
          v-model="message"
        />
        <input
          type="submit"
          value="提交"
          v-bind:disabled="message == ''"
          @click.prevent="addData"
          class="py-3 w-full bg-green-500 rounded-md text-center text-2xl text-gray-100 cursor-pointer hover:bg-green-700 active:translate-y-1 disabled:bg-gray-400"
        />
      </label>
    </form>
  </section>
</template>
