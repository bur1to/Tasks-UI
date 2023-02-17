<template>
<button class="btn">
    <slot></slot>
</button>
</template>

<script>
export default {
    name: 'my-button'
}
</script>

<style>
.btn {
    background: none;
    padding: 10px 15px;
    color: #6A5ACD;
    border: 1px solid #6A5ACD;
    margin-top: 20px;
    align-self: flex-start;
}

.btn:hover {
    background-color: #6A5ACD;
    color: white;
}
</style>
