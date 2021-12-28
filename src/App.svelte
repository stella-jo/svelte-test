<script>
	import Todos from './components/Todos.svelte';

	let newText = null;
	let todoList = [];
	let input = null;

	function add() {
		input.style.display = "block";
		input.focus();
	}
	function newTodo() {
		todoList = todoList.concat(newText);
		input.value = null;
		newText = null;
	}
	
	function blurFunction() {
		if (newText != null) {
			newTodo();
		}
		input.style.display = "none";
	}

	window.addEventListener("load", () => {
		input = document.querySelector(".todoInput");
		input.addEventListener("keydown", key => {
			if (key.key == "Enter") {
				if (newText != null) {
					newTodo();
				}
			}
		});
		const title = document.querySelector("h1");
		let date = new Date();
		title.textContent = `${date.getFullYear()}-${date.getMonth() + 1}-${date.getDate()}`;
	});
</script>

<header>
	<h1>투두리스트</h1>
	<button class = "editButton"><span></span><span></span><span></span></button>
</header>

<main>
	{#each todoList as item}
		<Todos>{item}</Todos>
	{/each}
	<input enterkeyhint = "done" bind:value = {newText} class = "todoInput" on:blur = {blurFunction} type = "text">
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
	.editButton {
		width: 28px;
		height: 24px;
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
		border-radius: 0px;
		padding: 8px 0px;
		display: none;
		font-size: 1rem;
	}
</style>