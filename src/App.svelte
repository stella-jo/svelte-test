<script>
	import Todos from './components/Todos.svelte';

	let newText = "";
	let todoList = [];

	function add() {
		const input = document.querySelector(".todoInput");
		input.style.display = "block";
		input.focus();
	}
	function newTodo() {
		const input = document.querySelector(".todoInput");
		todoList = todoList.concat(newText);
		input.value = null;
		input.style.display = "none";
	}
</script>

<header>
	<h1>To-do list</h1>
	<button class = "editButton"><span></span><span></span><span></span></button>
</header>

<main>
	{#each todoList as item}
		<Todos todo = {item} />
	{/each}
	<input bind:value = {newText} class = "todoInput" on:blur = {newTodo} type = "text">
	<button class = "addButton" on:click = {add}>할 일 추가</button>
</main>

<style>
	header {
		display: flex;
		justify-content: space-between;
		align-items: center;
		padding: 36px;
	}
	h1 {
		font-size: 2rem;
		color: #404040;
	}
	main {
		margin: 0px 36px;
		display: flex;
		flex-direction: column;
		gap: 16px;
	}
	button {
		border: none;
		background: none;
		text-align: left;
	}
	.addButton {
		color: #40404080;
	}
	.editButton span {
		display: block;
		position: relative;
		width: 28px;
		height: 2px;
		border-radius: 1px;
		background-color: #DC8F8F;
	}
	.editButton span:first-child {
		top: -8px;
	}
	.editButton span:last-child {
		top: 8px;
	}

	.todoInput {
		outline: none;
		border: none;
		border-bottom: 2px solid #DC8F8F;
		padding: 8px 0px;
		display: none;
		font-size: 1rem;
	}
</style>