<script>
    let { task, onToggle, onRemove } = $props();
</script>

<div class="task" class:completed={task.done}>
    <label>
        <input
            type="checkbox"
            checked={task.done}
            onchange={() => onToggle(task.id)}
        />

        <span>{task.title}</span>
    </label>

    <button
        type="button"
        onclick={() => onRemove(task.id)}
        aria-label={`Excluir ${task.title}`}
    >
        Excluir
    </button>
</div>

<style>
    .task {
        display: flex;
        justify-content: space-between;
        align-items: center;
        gap: 12px;
        padding: 14px;
        margin: 10px 0;
        background: white;
        border: 1px solid #ddd;
        border-radius: 8px;
    }

    label {
        display: flex;
        align-items: center;
        gap: 10px;
        overflow-wrap: anywhere;
    }

    .completed span {
        text-decoration: line-through;
        color: #777;
    }

    button {
        padding: 7px 10px;
        border: none;
        border-radius: 5px;
        background: #b42318;
        color: white;
        cursor: pointer;
    }
</style>