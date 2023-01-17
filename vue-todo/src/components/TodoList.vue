<template>
  <div>
    <ul>
      <li v-for="(item, index) in todoItems" v-bind:key="item.item" class="shadow">
        <!-- check 버튼 영역 -->
        <span v-bind:class="{checkBtnCompleted: item.completed}" v-on:click="toggleComplete(item)">
            <font-awesome-icon icon="fa-solid fa-check" />
        </span>
        <!-- list 영역 -->
        <span v-bind:class="{textCompleted: item.completed }">
            {{ item.item }}
        </span>
        <!-- delete 버튼 영역 -->
        <span class="removeBtn" v-on:click="removeTodo(item, index)">
          <font-awesome-icon icon="fa-solid fa-trash-can" />
        </span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      todoItems: []
    }
  },
  methods: {
    removeTodo: function(item, index) {
      localStorage.removeItem(item.item);
      this.todoItems.splice(index,1);
    },
    toggleComplete: function(item) {
      item.completed = !item.completed;
      localStorage.removeItem(item.item);
      localStorage.setItem(item.item,JSON.stringify(item));
    }
  },
  created: function() {
    if (localStorage.length > 0) {
      for(var i=0;i<localStorage.length;i++) {
        if(localStorage.key(i) !== 'loglevel:webpack-dev-server') {
          this.todoItems.push(JSON.parse(localStorage.getItem(localStorage.key(i))));
          // this.todoItems.push(localStorage.key(i));
        }
      }
    }
  }
}
</script>

<style>
  ul {
    list-style-type: none;
    padding-left:0px;
    margin-top:0;
    text-align: left;
  }

  li {
    display: flex;
    min-height:50px;
    height:50px;
    line-height: 50px;
    margin: 0.5rem 0;
    padding: 0 0.9rem;
    background: white;
    border-radius: 5px;
  }

  .checkBtn {
    line-height: 45px;
    color: #62acde;
    margin-left:5px;
  }

  .checkBtnCompleted {
    color: #b3adad
  }

  .textCompleted {
    text-decoration: line-through;
    color: #b3adad;
  }

  .removeBtn {
    margin-left: auto;
    color: #de4343;
  }

  .shadow {
    box-shadow: 5px 10px 10px rgba(0,0,0,0.03);
  }
</style>