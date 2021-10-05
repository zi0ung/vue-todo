<template>
    <div class="inputBox shadow">
        <input type="text" v-model="newTodoItem" placeholder="오늘의 할 일을 입력해 주세요." v-on:keyup.enter="addTodo" />
        <span class="addContainer" v-on:click="addTodo">
            <i class="addBtn fas fa-plus" aria-hidden="true"></i>
        </span>
    </div>
</template>

<script>
export default {
    data(){
        return {
            newTodoItem: ''
        }
    },
    methods: {
        addTodo(){
            //console.log(this.newTodoItem);
            // 입력받은 텍스트를 로컬 스토리지에 저장하기
            // 현재 데이터베이스 서버 없는 상태.
            // 자바스크립트에서 브라우저가 켜져있는 동안에
            // 임시로 데이터베이스 역할을 할 수 있게 해주는 내장객체
            // localSrotage
            // API 형식에서 setItem(key, value);

            if(this.newTodoItem !== ""){
                // input 태그에 빈 값 체크를 한 뒤,
                // 빈 값을 집어 넣되, 문장의 앞 뒤로 띄어 쓰기가 들어가는 경우.
                // 공백을 제거해주는 자바스크립트 내장 함수 trim();
                var value = this.newTodoItem && this.newTodoItem.trim();
                localStorage.setItem(value, value);
                this.$emit('addTodo', value);
                this.clearInput();
            }
        },
        clearInput(){
            this.newTodoItem = '';
        }
    }
}
</script>

<style>
    input:focus {
        outline: none;
    }
    .inputBox {
        background-color: #fff;
        height: 50px;
        line-height: 50px;
        border-radius: 5px;
    }
    .inputBox input {
        border-style: none;
        font-size: 0.9em;
    }
    .addContainer {
        float: right;
        background: linear-gradient(to right, #6478fb, #8763fb);
        display: block;
        width: 3rem;
        border-radius: 0 5px 5px 0;
    }
    .addBtn {
        color: #fff;
        cursor: pointer;
        display: block;
        height: 50px;
        line-height: 50px;
    }
</style>