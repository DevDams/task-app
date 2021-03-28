<template>
  <div class="content">
    <div class="form">
      <h2>MA LISTE DES TACHES</h2>
      <div class="formulaire">
        <form @submit.prevent="addTodo">
          <input v-model="Todo" type="text" name="newTodo" id="newTodo" placeholder="Ajouter une nouvelle tache ici">
          <button type="submit" name="button">
            <div class="ajouter">
              <svg version="1.1" id="Capa_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px"
                viewBox="0 0 309.059 309.059" style="enable-background:new 0 0 309.059 309.059;" xml:space="preserve">
                <g>
                  <g>
                  <path style="fill:#fff;" d="M280.71,126.181h-97.822V28.338C182.889,12.711,170.172,0,154.529,0S126.17,12.711,126.17,28.338
                    v97.843H28.359C12.722,126.181,0,138.903,0,154.529c0,15.621,12.717,28.338,28.359,28.338h97.811v97.843
                    c0,15.632,12.711,28.348,28.359,28.348c15.643,0,28.359-12.717,28.359-28.348v-97.843h97.822
                    c15.632,0,28.348-12.717,28.348-28.338C309.059,138.903,296.342,126.181,280.71,126.181z"/>
                </g></g><g></g><g></g><g></g><g></g><g></g><g></g><g></g><g></g><g></g><g></g><g></g><g></g><g></g><g></g><g></g>
              </svg>
            </div>
          </button>
        </form>
      </div>
      <div class="tout_cocher">
        <button @click="allDone" type="button" name="button">Tout marquer</button>
      </div>
    </div>
    <div class="list_item">
      <ul>
        <li v-for="todo in todos" :key="todo">
          <span :class=" { done: todo.done } ">{{ todo.content }}</span>
          <div class="action_btn">
            <!-- ===== CHECK BUTTON ===== -->
            <div class="check">
              <button @click="done(todo)" type="button" name="button">
                <div class="check_btn">
                  <svg version="1.1" id="Capa_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px"
                    width="405.272px" height="405.272px" viewBox="0 0 405.272 405.272" style="enable-background:new 0 0 405.272 405.272;"
                    xml:space="preserve">
                  <g>
                    <path style="fill:#fff;" d="M393.401,124.425L179.603,338.208c-15.832,15.835-41.514,15.835-57.361,0L11.878,227.836
                      c-15.838-15.835-15.838-41.52,0-57.358c15.841-15.841,41.521-15.841,57.355-0.006l81.698,81.699L336.037,67.064
                      c15.841-15.841,41.523-15.829,57.358,0C409.23,82.902,409.23,108.578,393.401,124.425z"/>
                  </g><g></g><g></g><g></g><g></g><g></g><g></g><g></g><g></g>
                  <g></g><g></g><g></g><g></g><g></g><g></g><g></g>
                  </svg>
                </div>
              </button>
            </div>
            <!-- ===== DELETE BUTTON ===== -->
            <div class="delete">
              <button @click="removeTodo(todo)" type="button" name="button">
                <div class="delete_btn">
                  <svg version="1.1" id="Capa_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px"
                    width="482.428px" height="482.429px" viewBox="0 0 482.428 482.429" style="enable-background:new 0 0 482.428 482.429;"
                    xml:space="preserve">
                  <g>
                    <g>
                      <path style="fill:#fff;" d="M381.163,57.799h-75.094C302.323,25.316,274.686,0,241.214,0c-33.471,0-61.104,25.315-64.85,57.799h-75.098
                        c-30.39,0-55.111,24.728-55.111,55.117v2.828c0,23.223,14.46,43.1,34.83,51.199v260.369c0,30.39,24.724,55.117,55.112,55.117
                        h210.236c30.389,0,55.111-24.729,55.111-55.117V166.944c20.369-8.1,34.83-27.977,34.83-51.199v-2.828
                        C436.274,82.527,411.551,57.799,381.163,57.799z M241.214,26.139c19.037,0,34.927,13.645,38.443,31.66h-76.879
                        C206.293,39.783,222.184,26.139,241.214,26.139z M375.305,427.312c0,15.978-13,28.979-28.973,28.979H136.096
                        c-15.973,0-28.973-13.002-28.973-28.979V170.861h268.182V427.312z M410.135,115.744c0,15.978-13,28.979-28.973,28.979H101.266
                        c-15.973,0-28.973-13.001-28.973-28.979v-2.828c0-15.978,13-28.979,28.973-28.979h279.897c15.973,0,28.973,13.001,28.973,28.979
                        V115.744z"/>
                      <path style="fill:#fff;" d="M171.144,422.863c7.218,0,13.069-5.853,13.069-13.068V262.641c0-7.216-5.852-13.07-13.069-13.07
                        c-7.217,0-13.069,5.854-13.069,13.07v147.154C158.074,417.012,163.926,422.863,171.144,422.863z"/>
                      <path style="fill:#fff;" d="M241.214,422.863c7.218,0,13.07-5.853,13.07-13.068V262.641c0-7.216-5.854-13.07-13.07-13.07
                        c-7.217,0-13.069,5.854-13.069,13.07v147.154C228.145,417.012,233.996,422.863,241.214,422.863z"/>
                      <path style="fill:#fff;" d="M311.284,422.863c7.217,0,13.068-5.853,13.068-13.068V262.641c0-7.216-5.852-13.07-13.068-13.07
                        c-7.219,0-13.07,5.854-13.07,13.07v147.154C298.213,417.012,304.067,422.863,311.284,422.863z"/>
                    </g>
                  </g><g></g><g></g><g></g><g></g><g></g><g></g>
                  <g></g><g></g><g></g><g></g><g></g><g></g><g></g><g></g><g></g>
                  </svg>
                </div>
              </button>
            </div>
          </div>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      Todo: '',
      todos: []
    }
  },
  mounted() {
    if(localStorage.getItem("todos")) {
      this.todos = JSON.parse(localStorage.getItem("todos"))
    } else {
      console.log("no notes save")
    }
  },
  methods: {
    // Add a new todo item
    addTodo() {
      this.todos.push({content: this.Todo, done: false})
      localStorage.setItem("todos", JSON.stringify(this.todos))
      this.Todo = ''
    },
    // Remove a todo item
    removeTodo(todo) {
      const todoIndex = this.todos.indexOf(todo)
      this.todos.splice(todoIndex, 1)
      localStorage.setItem("todos", JSON.stringify(this.todos))
    },
    // Mark a todo item as done
    done(todo) {
      let list_item = document.querySelector('.list_item')
      list_item.classList.toggle("check")
      const todoIndex = this.todos.indexOf(todo)
      this.todos[todoIndex].done = !this.todos[todoIndex].done
      localStorage.setItem("todos", JSON.stringify(this.todos))
    },
    // Mark all the todo item as done
    allDone() {
      this.todos.forEach(todo => {
        todo.done = true
      })
      localStorage.setItem("todos", JSON.stringify(this.todos))
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
ul li {
  list-style: none;
}

h2 {
  text-align: center;
  color: #0d0d0d;
}

/* Hide scrollbar for Chrome, Safari and Opera */
.content::-webkit-scrollbar {
    display: none;
}

.content {
  overflow-y: scroll;
  -ms-overflow-style: none;
  scrollbar-width: none;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 450px;
  height: 600px;
  border-radius: 15px;
  box-shadow: 0px 5px 30px -10px #073b4c;
  background-color: #efefef;
}

.form {
  width: 100%;
  height: 220px;
  background-color: #efefef;
  position: sticky;
  padding-top: 1px;
  top: 0;
  z-index: 10;
}

.formulaire {
  display: flex;
  justify-content: center;
}

.formulaire form {
  width: 80%;
  display: flex;
  align-items: center;
  justify-content: space-around;
}

.formulaire form input {
  height: 45px;
  width: 300px;
  border-radius: 30px;
  border: none;
  outline: none;
  text-align: center;
  background: #073b4c;
  color: #efefef;
}

.formulaire form input::placeholder {
  color: #efefef;
  font-family: 'Montserrat', sans-serif;
}

.formulaire form input:focus {
  background-color: #073b4cd2;
}

.formulaire form input:focus::placeholder {
  opacity: .4;
}

.formulaire form button {
  cursor: pointer;
  border: none;
  border-radius: 50%;
  outline: none;
  background-color: #118ab2;
  transition: all .1s ease-in-out;
}

.formulaire form button:hover {
  opacity: .7;
}

.ajouter {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 25px;
  height: 35px;
}

.ajouter svg {
  width: 18px;
}

.tout_cocher {
  display: flex;
  justify-content: center;
  margin-top: 20px;
}

.tout_cocher button {
  font-family: 'Montserrat', sans-serif;
  font-weight: 700;
  text-transform: uppercase;
  background-color: #06d6a0;
  border: none;
  border-radius: 10px;
  outline: none;
  padding: 10px 20px;
  cursor: pointer;
  transition: all .2s ease-in-out;
}

.tout_cocher button:hover {
  background-color: #06d69ebe;
}


.list_item {
  top: 50px;
}

.list_item ul li {
  position: relative;
  background: #fff;
  width: inherit;
  height: 70px;
  left: -20px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin: 15px 0;
  padding: 0 15px;
  border-radius: 10px;
  box-shadow: 0 5px 15px -5px rgba(67, 67, 67, 0.2);
}

.list_item ul li .action_btn {
  width: 80px;
  display: flex;
  justify-content: space-between;
}

.list_item ul li .delete button {
  background-color: #ff476f;
  border: none;
  outline: none;
  padding: 5px;
  border-radius: 10px;
  cursor: pointer;
}

.list_item ul li .check button {
  background-color: #06d6a0;
  border: none;
  outline: none;
  padding: 5px;
  border-radius: 10px;
  cursor: pointer;
}

.list_item ul li button svg {
  width: 24px;
  height: 24px;
}

.done {
  text-decoration: line-through;
  opacity: .4;
}
</style>
