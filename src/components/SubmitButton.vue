<template>
    <button type="button" class="no-outline button" @click="$emit('click-action')">
        <span class="button-text"><slot></slot></span>
    </button>
</template>

<script>
export default {
  name: 'submitButton',
};
</script>

<style  lang="scss" >
    .button{
        border: none;
        cursor: pointer;
        font-family: 'Roboto', sans-serif;
        font-weight: bold;
        font-size: 1rem;
        min-width: 18.75rem;
        max-width: 21.875rem;
        letter-spacing: 0.2px;
        color: #fff;
        background-color: #4fbfa6;
        margin: 1.25rem 0.625rem;
        padding: 0.875rem 0.75rem;
        border-radius: 0.3125rem;
        box-sizing: border-box;
        -moz-box-sizing: border-box;
        transition: 5s all;
        position: relative;
        overflow: hidden;
        &::before{
            content: "";
            transition: 0.8s all;
            width: 0;
            position: absolute;
            top:0;
            left: -1.875rem;
            height: 100%;
            background-color: #2e8a76;
            transform: skew(-10deg);
        }
        &:hover.button::before{
            width: 150%;
        }
        .button-text{
            position: relative;
            z-index: 1;
        }
    }
</style>
