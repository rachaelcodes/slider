<template>
  <div class="sl-element" :class="num"></div>
</template>
<script>
export default {
  props: ['num']
}
</script>
<style>
.sl-element {
    height: 400px;
    width: 400px;
}

.one {
    background-image: url("http://placehold.it/750x457")
}

.two {
    background-image: url("http://placehold.it/360x221")
}

.three {
    background-image: url("http://placehold.it/263x160")
}
</style>
