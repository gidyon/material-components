<template>
    <div class="jumbotron fh fw" style="display: none;">
        <div class="fh fw relative">
            <img src="/static/doc-images/carousel/sky.jpg" class="jumbotron__image">
            <div class="jumbotron__background"></div>
            <div class="jumbotron__content">
                
            </div>
        </div>
    </div>
</template>

<style lang="scss" scoped>
    .jumbotron__image {
        position: absolute;
        top: 50%;
        left: 50%;
        -webkit-transform: translate(-50%,-50%);
        transform: translate(-50%,-50%);
        min-width: 100%;
        will-change: transform;
    }
    img {
        border-style: none;
    }
    .jumbotron__background {
        position: absolute;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        contain: strict;
    }
    .jumbotron__background, .jumbotron__wrapper {
        -webkit-transition: inherit;
        transition: inherit;
    }
</style>

