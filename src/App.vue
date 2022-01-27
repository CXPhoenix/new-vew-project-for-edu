<script>
import { ref } from "vue";
import TODOHeader from "./components/TODOHeader.vue";
import TODOForm from "./components/TODOForm.vue";
import TODOList from "./components/TODOList.vue";
export default {
  components: { TODOHeader, TODOForm, TODOList },
  setup() {
    const datas = ref([]);

    const addData = function (message) {
      if (message == "") {
        return;
      }
      datas.value.push(message);
      message = "";
    };

    const deleteItem = function(datas, index) {
      datas.splice(index, 1);
    }

    return {
      datas,
      addData,
      deleteItem
    };
  },
};
</script>

<template>
  <TODOHeader title="代辦事項" />
  <TODOForm :addDataFunction="addData" />
  <TODOList :datas="datas" :deleteItem="deleteItem" />
  <footer class="uppercase text-center fixed bottom-0 inset-x-0 bg-gray-200/50">
    power by cxphoenix
  </footer>
</template>

<style></style>
