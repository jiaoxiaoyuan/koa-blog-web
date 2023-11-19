<template>
    <div class="animate">
        <BackgroundView></BackgroundView>
        <h1>Hello World</h1>
    </div>
</template>

<script >
import BackgroundView from './components/BackgroundView';

</script>

<style scoped lang="scss">
.animate {
    transform: scale(1);
    transition: all ease 1.25s;
    opacity: 1;
    filter: blur(0);
    width: 100%;
    height: 100%;
}
</style>
