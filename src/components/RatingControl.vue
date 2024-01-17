<template>
    <div>
        <button @click="selectValue('1')" :class="{
            active: modelValue === '1'
        }">1</button>
        <button @click="selectValue('2')" :class="{
            active: modelValue === '2'
        }">2</button>
        <button @click="selectValue('3')" :class="{
            active: modelValue === '3'
        }">3</button>
    </div>
</template>

<script>
export default {
    props: ['modelValue'],
    emits: ['update:modelValue'],
    methods: {
        selectValue(value) {
            this.$emit('update:modelValue', value)
        }
    }
}
</script>
<style scoped>
.active {
    background-color: red;
    color: white;
}
</style>