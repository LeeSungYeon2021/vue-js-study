<template>
  <div class="inputBox shadow">
    <input type="text" v-model="newTodoItem" v-on:keyup.enter="addTodo">
    <span class="addContainer" v-on:click="addTodo">
      <font-awesome-icon icon="fa-solid fa-square-plus" size="3x" />
    </span>
    <TodoModal  v-if="showModal" @close="showModal=false">
        <!-- slot : 특정 컴포넌트의 재사용 할 수 있는 속성 -->
        <h3 slot=header>Header!</h3>  
        <h3 slot="body">Body!</h3>  
        <h3 slot="footer">Footer!</h3>  
    </TodoModal>
  </div>
</template>

<script>
import TodoModal  from './common/TodoModal.vue'

export default {
  data: function() {
    return {
      newTodoItem: "",
      showModal: false
    }
  },
  methods: {
    addTodo: function() {
      if(this.newTodoItem !== '') {
        // this.$emit('이벤트 이름',인자1,인자2...);
        this.$emit('addTodoItem',this.newTodoItem);
        this.clearInput();
      }else {
        this.showModal = !this.showModal;
      }
    },
    clearInput: function() {
      // 클릭 후 공백처리
      this.newTodoItem = "";
    },
    components: {
      'TodoModal':TodoModal,
    }
  }
}
</script>

<style scoped>
  input:focus {
    outline: none;
  }
  .inputBox {
    background:white;
    height:50px;
    line-height: 50px;
    border-radius: 5px;
  }
  .inputBox input {
    border-style:none;
    font-size:0.9rem;
  }
  .addContainer {
    float:right;
    background:linear-gradient(to right,#6478FB,8763FB);
    display:block;
    width: 3rem;
    height:3rem;
    border-radius: 0 5px 5px 0;
  }
  .addBtn {
    color:white;
    vertical-align: middle;
  }
  .shadow {
    box-shadow: 5px 10px 10px rgba(0,0,0,0.03);
  }
</style>