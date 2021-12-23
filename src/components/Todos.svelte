<script>
    export let todo;
</script>

<span>
    <input type = "checkbox" id = "todo">
    <label for = "todo">{todo}</label>
</span>

<style>
    span {
        color: #404040;
        display: flex;
        gap: 8px;
        align-items: center;
        width: max-content;
    }

    /* input {
        appearance: none;
    } */
</style>