<script>

  // TODO manage routing to /login and /signup
  import { fly } from "svelte/transition";

  var ongoing_todos = [];
  var completed_todos = [];
  let todo = "";

  const add = (todo) => {
    if(ongoing_todos.indexOf(todo) !== -1){
      alert('Item already in list!!')
    }else{
      ongoing_todos = [...ongoing_todos, todo];
      todo = "";
    }
  };

  const tick = (todo) => {
    completed_todos = [...completed_todos, todo];
    ongoing_todos = ongoing_todos.filter(function (item) {
      return item !== todo;
    });
    ongoing_todos = [...ongoing_todos];
  };

  // TODO accept json data from api
  const exportData = () => {
    const js = {
      "ongoing": [...ongoing_todos],
      "completed": [...completed_todos]
    }
  }

</script>

<main>
  <h1>STodo list</h1>
  <div class="form-container">
    <input
      class="text"
      type="text"
      placeholder="Enter todo"
      bind:value={todo}
    />
    <button class="primary" on:click={() => add(todo)}>Add</button>
    <button class="secondary">Export</button>
    <button class="ternary">Import</button>
  </div>

  <div class="parent">
    <div class="row">
      <div class="child">
        <h3>Ongoing</h3>
        {#each ongoing_todos as list}
          <div class="checkboxes" in:fly>
            <label
              ><input
                type="checkbox"
                on:click={() => tick(list)}
              /> <span>{list}</span></label
            >
          </div>
        {/each}
      </div>
      <div class="child">
        <h3>Completed</h3>
        {#each completed_todos as list}
          <div class="checkboxes">
            <label class="checked"
              ><input
                type="checkbox"
                on:click={() => tick(list)}
                checked
                disabled
              /> <span>{list}</span></label
            >
          </div>
        {/each}
      </div>
    </div>
  </div>
</main>

<style>
  .form-container {
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .parent {
    display: flex;
    flex-direction: column;
  }

  .row {
    display: flex;
    flex-direction: column;
  }

  .child {
    width: 120%;
    height: 200px;
    overflow-y: scroll;
    background-color: rgb(115, 182, 52);
    color: white;
    text-align: center;
    margin: 10px 10px 10px 10px;
  }

  .text {
    width: 100%;
    padding: 12px 20px;
    margin: 8px 8px;
    box-sizing: border-box;
  }

  .primary {
    background-color: black;
    color: white;
    width: 30%;
    margin-right: 6px;
  }

  .primary:hover {
    background-color: white;
    color: black;
    border-color: black;
    border-width: 1px;
  }

  .secondary {
    background-color: rgb(83, 89, 160);
    color: white;
    width: 30%;
    margin-right: 6px;
  }

  .secondary:hover {
    color:rgb(83, 89, 160);
    background-color: white;
    border-color: lightblue;
    border-width: 1px;
  }

  .ternary {
    background-color: rgba(118, 216, 147, 0.863);
    border-style: none;
    width: 30%;
  }

  .ternary:hover {
    color: rgba(55, 179, 92, 0.863);
    background-color: white;
    border-color: rgb(85, 211, 60);
    border-width: 1px;
  }

  .checked {
    text-decoration: line-through;
  }

  .checkboxes label {
    display: flex;
  }
  .checkboxes input {
    margin: 8px 0px;
    margin-right: 6px;
    margin-left: 8px;
  }

  .checkboxes label span {
    vertical-align: middle;
  }

  ::-webkit-scrollbar {
    width: 1px;
  }

  ::-webkit-scrollbar-track {
    background: #f1f1f1;
  }

  ::-webkit-scrollbar-thumb {
    background: #888;
  }

  ::-webkit-scrollbar-thumb:hover {
    background: #555;
  }
</style>
