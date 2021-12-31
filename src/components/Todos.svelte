<script>
    export let index, removeTodo;
    export let check = false;
</script>

<div class = "box">
    <form>
        <input id = {index} type = "checkbox" bind:checked = {check}>
        <label for = {index}>
            <slot></slot>
        </label>
    </form>
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
        gap: 8px;
        align-items: center;
    }
    form {
        display: flex;
        gap: 8px;
        word-break: break-all;
        align-items: center;
    }
    label {
        color: #404040;
    }
    input:checked ~ label {
        text-decoration: line-through;
        opacity: 70%;
    }
    input {
        appearance: none;
        -webkit-appearance: none;
        width: 16px;
        height: 16px;
        background-color: #ffffff;
        border: 2px solid #40404050;
        border-radius: 6px;
    }
    input:checked {
        background-color: #DC8F8F50;
        border-color: #DC8F8F;
    }
    @media screen and (min-device-width: 769px) {
        button {
            display: none;
        }
        .box:hover button {
            display: block;
        }
    }
</style>