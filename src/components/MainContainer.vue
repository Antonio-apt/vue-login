<template>
    <div id="main-container">
        <slot class="slot"></slot>
    </div>
</template>

<script>
export default {
  name: 'mainContainer',
};
</script>

<style  lang="scss" >
    #main-container {
        display: flex;
        top: 6.25rem;
        align-items: center;
        flex-direction: column;
        position: relative;
        min-width: 7.5rem;
    }
</style>
