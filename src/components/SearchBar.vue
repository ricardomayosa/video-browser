<template>
    <div>
        <!-- <input v-on:input="onInput" type="text"> -->
        <input @input="onInput" type="text">
    </div>
</template>

<script>
export default {
    /* eslint-disable */
    name: 'SearchBar',
    methods: {
        onInput: function(e) {
            this.$emit('termChange', e.target.value);
        }
    }
};
</script>

<style scoped>
input {
    width: 75%;
}
div {
    text-align: center;
    margin: 30px;
}
</style>
