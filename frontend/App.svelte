<script>
  import './App.css';
  import { onMount } from 'svelte';
  let todos = [];
  let newTodo = '';
  let api = 'http://localhost:4000/api/todos';

  async function fetchTodos() {
    const res = await fetch(api);
    todos = await res.json();
  }

  async function addTodo() {
    if (!newTodo.trim()) return;
    const res = await fetch(api, {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({ text: newTodo })
    });
    if (res.ok) {
      newTodo = '';
      fetchTodos();
    }
  }

  async function toggleTodo(todo) {
    await fetch(`${api}/${todo._id}`, {
      method: 'PUT',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({ text: todo.text, completed: !todo.completed })
    });
    fetchTodos();
  }

  async function deleteTodo(id) {
    await fetch(`${api}/${id}`, { method: 'DELETE' });
    fetchTodos();
  }

  onMount(fetchTodos);
</script>

<main>
  <h1>TODO List</h1>
  <form on:submit|preventDefault={addTodo}>
    <input bind:value={newTodo} placeholder="Add a todo..." />
    <button type="submit">Add</button>
  </form>
  <ul>
    {#each todos as todo}
      <li class:completed={todo.completed}>
        <input type="checkbox" checked={todo.completed} on:change={() => toggleTodo(todo)} />
        {todo.text}
        <button on:click={() => deleteTodo(todo._id)}>Delete</button>
      </li>
    {/each}
  </ul>
</main>
