<template>
    <div class="sl-wrapper">
        <div class="sl-element" :class="num">
        </div>
        <div class="sl-text">
            <p v-if="num==='one'">Photo by <a href="https://unsplash.com/photos/umqw42faoBU?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Evan McDougall</a> on <a href="https://unsplash.com/search/photos/nature?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a></p>
            <p v-if="num==='two'">Photo by <a href="https://unsplash.com/photos/FYtVrif82Lw?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Geran de Klerk</a> on <a href="https://unsplash.com/search/photos/nature?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a></p>
            <p v-if="num==='three'">Photo by <a href="https://unsplash.com/photos/Dksk8szLRN0?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Sora Sagano</a> on <a href="https://unsplash.com/search/photos/nature?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a></p>
        </div>
    </div>
</template>
<script>
export default {
  props: ['num']
}
</script>
<style>
.sl-element {
    height: 350px;
    width: 350px;
    margin: auto;
}

.one {
    background-image: url("../assets/bird.jpg")
}

.two {
    background-image: url("../assets/deer.jpg")
}

.three {
    background-image: url("../assets/fish.jpg")
}
</style>
