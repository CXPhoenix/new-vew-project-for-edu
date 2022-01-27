<script>
export default {
  props: ["datas", "deleteItem"],
  setup(props) {
    const datas = props.datas;
    const deleteItem = props.deleteItem;
    return {
      datas,
      deleteItem,
    };
  },
};
</script>

<template>
  <section id="reader" class="mt-12 mb-8 space-y-4">
    <div
    v-for="(data, index) in datas" :key="index"
      class="w-9/12 px-3 mx-auto flex justify-between items-center border-2 border-gray-300 rounded-md"
    >
      <h2 class="text-2xl">{{ index + 1 }}.&nbsp;&nbsp;{{ data }}</h2>
      <font-awesome-icon
        icon="times-circle"
        @click="deleteItem(datas, index)"
        class="text-red-600/40 text-2xl cursor-pointer hover:text-red-600"
      />
    </div>
  </section>
</template>
