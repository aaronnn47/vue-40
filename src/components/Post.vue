<template>
  <div>
    <p>Author: {{postObject.author}} </p>
    <p>{{postObject.post}}</p>
    <hr>
  </div>
</template>

<script>
export default {
  props: ['postObject']
};
</script>
