<script>
export default {
  props: ['title', 'textClassName'],
  setup(props) {
    const title = props.title;
    let textClassName = props.textClassName;
    if (!textClassName) {
        textClassName = "text-center text-[3rem] text-gray-800"
    }
    return { title, textClassName };
  },
};
</script>

<template>
  <header class="p-10 bg-blue-200 mb-2">
    <h1 :class="textClassName">{{ title }}</h1>
  </header>
</template>
