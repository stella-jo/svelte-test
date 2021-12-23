<script>
    export let todo;
</script>

<form>
    <input type = "checkbox" id = "todo">
    <label for = "todo">{todo}</label>
</form>

<style>
    form {
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