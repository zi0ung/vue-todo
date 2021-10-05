<template>
    <section>
        <ul>
            <li v-for="(todoItem, index) in propsdata" :key="todoItem" class="shadow">
                <span>
                    <i class="checkBtn fas fa-check"></i>
                </span>
                {{ todoItem }}
                <span class="removeBtn" @click="removeTodo(todoItem, index)">
                    <i class="far fa-trash-alt" aria-hidden="true"></i>
                </span>
            </li>
        </ul>
    </section>
</template>

<script>
export default {
    props: ['propsdata'],
    methods: {
        removeTodo(todoItem, index){
            //console.log(todoItem, index);
            // 자바스크립트 로컬스토리지 객체에서 해당 데이터를 삭제하는 함수 removeItem();
            // todoItem에서 index를 가져와 삭제.
            // splice(index, 1); - 인덱스 삭제 함수.
            localStorage.removeItem(todoItem);
            this.todoItems.splice(index, 1);
        }
    }
}
</script>

<style scoped>
    ul {
        list-style: none;
        padding-left: 0px;
        margin-top: 0px;
        text-align: left;
    }
    li {
        display: flex;
        min-height: 50px;
        height: 50px;
        line-height: 50px;
        margin: 0.5rem 0;
        padding-left: 0 0.9rem;
        background-color: #fff;
        border-radius: 5px;
    }
    .checkBtn {
        color: #62acde;
        margin: 0 5px;
    }
    .removeBtn {
        margin-left: auto;
        color: #de4343;
        margin-right: 5px;
        cursor: pointer;
    }
</style>