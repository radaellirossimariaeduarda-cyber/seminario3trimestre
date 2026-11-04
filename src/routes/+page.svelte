<!--<h1>Welcome to SvelteKit</h1>-->
<!--<p>Visit <a href="https://svelte.dev/docs/kit">svelte.dev/docs/kit</a> to read the documentation</p> -->    
<script>
    import { untrack } from "svelte";
    import TaskItem from "../lib/TaskItem.svelte";

    /**
     * @typedef {{ id: number, title: string, done: boolean }} Task
     */

    /**
     * @type {{ data: { initialTasks: Task[] } }}
     */
    let { data } = $props();

    /** @type {Task[]} */
    let tasks = $state(
        untrack(() => data.initialTasks)
    );

    let newTask = $state("");

    let completedCount = $derived(
        tasks.filter(task => task.done).length
    );

    function addTask() {
        const title = newTask.trim();

        if (!title) return;

        const nextId = Math.max(
            0,
            ...tasks.map(task => task.id)
        ) + 1;

        tasks = [
            ...tasks,
            { id: nextId, title, done: false }
        ];

        newTask = "";
    }

    /** @param {number} id */
    function toggleTask(id) {
        tasks = tasks.map(task =>
            task.id === id
                ? { ...task, done: !task.done }
                : task
        );
    }

    /** @param {number} id */
    function removeTask(id) {
        tasks = tasks.filter(task => task.id !== id);
    }
</script>

<svelte:head>
    <title>Seminário 3º Trimestre | SvelteKit</title>
    <meta
        name="description"
        content="Demonstração prática do Svelte e SvelteKit desenvolvida para o seminário de WEB 1."
    />
</svelte:head>

<main>
    <header>
        <h1>Seminário 3º Trimestre</h1>
        <h2>Demonstração prática: Svelte e SvelteKit</h2>
        <p>
            Aplicação de gerenciamento de tarefas desenvolvida
            para demonstrar os recursos do framework.
        </p>
    </header>

    <form
        onsubmit={(event) => {
            event.preventDefault();
            addTask();
        }}
    >
        <label for="new-task">Adicionar nova tarefa</label>

        <div class="form-row">
            <input
                id="new-task"
                type="text"
                placeholder="Digite uma tarefa..."
                bind:value={newTask}
            />
            <button type="submit">Adicionar</button>
        </div>
    </form>

    <section aria-labelledby="tasks-title">
        <h2 id="tasks-title">Lista de tarefas</h2>

        <p class="counter">
            Tarefas concluídas: {completedCount} de {tasks.length}
        </p>

        {#if tasks.length > 0}
            {#each tasks as task (task.id)}
                <TaskItem
                    {task}
                    onToggle={toggleTask}
                    onRemove={removeTask}
                />
            {/each}
        {:else}
            <p class="empty">Nenhuma tarefa cadastrada.</p>
        {/if}
    </section>

    <footer>
        <a href="/sobre">Conheça o projeto</a>
        <p>Desenvolvido para o seminário de WEB 1.</p>
    </footer>
</main>

<style>
    :global(body) {
        margin: 0;
        font-family: Arial, sans-serif;
        background: #f3f5f9;
        color: #202938;
    }

    main {
        width: min(600px, calc(100% - 32px));
        margin: 40px auto;
        padding: 28px;
        box-sizing: border-box;
        background: white;
        border-radius: 14px;
        box-shadow: 0 4px 20px #00000010;
    }

    header {
        text-align: center;
        margin-bottom: 28px;
    }

    h1 {
        color: #5b42c3;
        margin-bottom: 10px;
    }

    header h2 {
        font-size: 19px;
        color: #384152;
    }

    header p {
        color: #687386;
        line-height: 1.5;
    }

    form {
        display: grid;
        gap: 10px;
    }

    .form-row {
        display: flex;
        gap: 8px;
    }

    input[type="text"] {
        flex: 1;
        min-width: 0;
        padding: 11px;
        border: 1px solid #ccc;
        border-radius: 6px;
    }

    .form-row button {
        padding: 11px 14px;
        border: none;
        border-radius: 6px;
        background: #5b42c3;
        color: white;
        cursor: pointer;
    }

    .form-row button:hover {
        background: #4932a5;
    }

    section {
        margin-top: 28px;
    }

    .counter {
        color: #5b42c3;
        font-weight: bold;
    }

    .empty {
        padding: 15px;
        text-align: center;
        color: #777;
    }

    footer {
        margin-top: 25px;
        text-align: center;
    }

    footer a {
        color: #5b42c3;
        font-weight: bold;
    }

    footer p {
        color: #777;
        font-size: 13px;
    }

    @media (max-width: 420px) {
        .form-row {
            flex-direction: column;
        }
    }
</style>
