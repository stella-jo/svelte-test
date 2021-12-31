<script>
	import Todos from './components/Todos.svelte';

	let newText = null;
	let todoList = [];
	let input = null;

	function removeTodo(index) {
		todoList = todoList.filter(todo => todo != todoList[index]);
	}

	function add() {
		input.style.display = "block";
		input.focus();
	}
	function newTodo() {
		todoList = todoList.concat({task: newText, checked: false});
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

<div class = "container">
	<header>
		<h1>2022-01-01</h1>
	</header>

	<main>
		{#each todoList as item, index}
			<Todos {index} bind:check = {todoList[index].checked} {removeTodo}>{item.task}</Todos>
		{/each}
		<input enterkeyhint = "done" bind:value = {newText} class = "todoInput" on:blur = {blurFunction} type = "text">
		<button class = "addButton" on:click = {add}>
			<svg width="12" height="12" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
			<rect x="10" y="3" width="4" height="18" rx="1" fill="#DC8F8F"/>
			<rect x="3" y="10" width="18" height="4" rx="1" fill="#DC8F8F"/>
			</svg>할 일 추가</button>
	</main>
</div>

<style>
	.container {
		background-color: #ffffff;
		display: flex;
		flex-direction: column;
		gap: 36px;
		padding: 36px;
		max-height: 100vw;
		max-height: 100vh;
	}

	header {
		display: flex;
		justify-content: space-between;
		align-items: center;
	}
	h1 {
		font-size: 2rem;
		color: #404040;
	}
	main {
		display: flex;
		flex-direction: column;
		gap: 16px;
		overflow: scroll;
	}
	.addButton {
		color: #40404080;
		display: flex;
		align-items: center;
		gap: 4px;
		width: fit-content;
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

	@media screen and (min-device-width: 769px) {
		.container {
			width: 400px;
			height: 600px;
			border-radius: 36px;
			position: absolute;
			top: 50%;
			left: 50%;
			transform: translate(-50%, -50%);
			box-shadow: 0 0 8px 4px #40404010;
		}
	}
</style>