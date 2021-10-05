<template>
    <div class="clearAllContainer">
        <span class="clearAllBtn shadow" @click="clearTodo">Clear All</span>
    </div>
</template>

<script>
export default {
    methods: {
        clearTodo(){
            // 로컬스토리지에 담긴 모든 데이터를 한번에 삭제.
            this.$emit('removeAll');
        }
    }
}
</script>

<style scoped>
    .clearAllContainer {
        height: 50px;
        line-height: 50px;
        background-color: #fff;
        border-radius: 5px;
        margin: auto;
    }
    .clearAllBtn {
        color: #e20303;
        display: block;
        cursor: pointer;
    }
</style>