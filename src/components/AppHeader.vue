<script setup>
defineProps(["charColor"])
</script>

<template>
    <header>
        <h2 v-bind:style="{color: charColor}"><slot></slot></h2>
    </header>
</template>