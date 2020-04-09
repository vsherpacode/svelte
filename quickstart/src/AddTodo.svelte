<script>
  import { createEventDispatcher } from 'svelte';
  let description;

  let addDispatcher = createEventDispatcher();

  const todoSubmit = (event) => {
    event.preventDefault();
    addDispatcher('addTodo', { description });
  };
</script>

<form class="add-todo" on:submit={todoSubmit}>
  <input type="text" bind:value={description} placeholder="Create new todo..." />
  <input class="add-button" type="submit" value="+" />
</form>


<style>
  form.add-todo {
    margin-top: 10px;
    display: flex;
  }
</style>