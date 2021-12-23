<script>
	import Todos from './components/Todos.svelte';

	const input = document.querySelector("input");
	function add() {
		input.style.display = "block";
	}
</script>

<header>
	<h1>2021-12-22</h1>
	<button onclick = "add()"><svg width="28" height="28" viewBox="0 0 28 28" fill="none" xmlns="http://www.w3.org/2000/svg">
		<rect x="13" width="2" height="28" rx="1" fill="#404040"/>
		<rect y="13" width="28" height="2" rx="1" fill="#404040"/>
	</svg></button>
</header>

<main>
	<input type = "text">
	<Todos todo = "영어 공부하기" />
	<Todos todo = "설거지하기" />
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
	}
	input {
		display: none;
	}
</style>