<script>
  import { createEventDispatcher } from 'svelte';
  export let description = "default description",
    index;

  const deleteDispatcher = createEventDispatcher();
  
  const deleteClicked = () => {
    deleteDispatcher('deleteClicked', { index });
  };
</script>


<div class="todo-item">
  <input type="checkbox">
  <div>{description}</div>
  <button on:click={deleteClicked}>x</button>
</div>

<style>
  .todo-item {
    padding: 5px;
    display: flex;
    align-items: baseline;
    justify-content: space-between;
  }

  .todo-item > input {
    margin-left: 10px;
    max-width: 10px;
  }

  .todo-item:nth-child(odd) {
    background-color: lightgrey;
  }

  .todo-item > div {
    width: 85%;
  }

  .todo-item > button {
    background-color: inherit;
    border: none;
    font-weight: 400;
    font-size: 20px;
  }

  .todo-item > button:hover {
    cursor: pointer;
  }
</style>


