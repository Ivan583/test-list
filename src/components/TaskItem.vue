<template>
  <li>{{ elem.id }} - {{ elem.title }} - {{ elem.description}}</li>
</template>

<script>
export default {
  props: {
    elem: {
      type: Object,
      required: true
    }
  }
};
</script>
