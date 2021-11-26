<template>
    <button @click="addNew()" :style="{ background: color }" class="btn">{{ text }}</button>
</template>

<script>
export default{
    name: 'Button',
    props: {
        text: String,
        color: String,
    },
    methods: {
        addNew() {
            this.$emit('toggle-add-task')
        }
    }
}
</script>