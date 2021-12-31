<script>
    export let index, removeTodo;
    export let check = false;
    setTimeout(() => {
        console.log(check);
    }, 10000);
</script>

<div class = "box">
    <label>
        <input type = "checkbox" bind:checked = {check}>
        <slot></slot>
    </label>
    <button on:click = {removeTodo(index)}>
        <svg width="12" height="12" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
        <rect x="3.51472" y="6.34315" width="4" height="20" rx="1" transform="rotate(-45 3.51472 6.34315)" fill="#DC8F8F"/>
        <rect x="3.51472" y="17.6569" width="20" height="4" rx="1" transform="rotate(-45 3.51472 17.6569)" fill="#DC8F8F"/>
        </svg>
    </button>
</div>

<style>
    .box {
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
    button {
        border: none;
        background: none;
    }

    /* input {
        appearance: none;
    } */
    @media screen and (min-device-width: 769px) {
        button {
            display: none;
        }
        .box:hover button {
            display: block;
        }
    }
</style>