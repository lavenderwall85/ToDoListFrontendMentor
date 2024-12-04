<script>
    let newTask = ''; 
    let tasks = []; 
    let filter = 'all'; 

    // Función para agregar tarea
    function addTask() {
        if (newTask.trim() !== '') {
            tasks.push({ text: newTask, completed: false });
            newTask = ''; 
        }
    }

    // Función para marcar tarea como completada
    function toggleCompletion(index) {
        tasks[index].completed = !tasks[index].completed;
    }

    // Función para filtrar tareas
    function filterTasks() {
        if (filter === 'all') {
            return tasks;
        } else if (filter === 'active') {
            return tasks.filter(task => !task.completed);
        } else if (filter === 'completed') {
            return tasks.filter(task => task.completed);
        }
        return tasks;
    }

    // Contador reactivo de tareas activas
    $: activeTasksCount = tasks.filter(task => !task.completed).length;
</script>

<style>
    :global(body) {
        margin: 0;
        font-family: 'Arial', sans-serif;
        background: linear-gradient(to right, #5c258d, #4389a2);
        color: #fff;
        height: 100vh;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .todo-app {
        width: 90%;
        max-width: 600px;
        background: rgba(0, 0, 0, 0.5);
        border-radius: 10px;
        padding: 20px;
        box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3);
    }

    .header {
        font-size: 1.5rem;
        text-align: center;
        margin-bottom: 20px;
    }

    .input-container {
        display: flex;
        gap: 10px;
    }

    .input-container input {
        flex: 1;
        padding: 10px;
        border: none;
        border-radius: 5px;
        font-size: 1rem;
    }

    .input-container input:focus {
        outline: none;
    }

    .todo-list {
        margin-top: 20px;
        list-style: none;
        padding: 0;
    }

    .todo-item {
        padding: 10px;
        background: rgba(255, 255, 255, 0.1);
        border-radius: 5px;
        margin-bottom: 10px;
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

    .todo-item span {
        flex: 1;
    }

    .todo-item button {
        background: none;
        border: none;
        color: #fff;
        cursor: pointer;
        font-size: 1rem;
    }

    .footer {
        margin-top: 20px;
        display: flex;
        justify-content: space-between;
        font-size: 0.9rem;
    }

    .filter-btn {
        cursor: pointer;
    }

    /* Estilos para el botón Add */
    button {
        padding: 10px 20px;
        background-color: #4389a2;
        border: none;
        color: white;
        font-size: 1rem;
        border-radius: 5px;
        cursor: pointer;
        transition: background-color 0.3s ease, transform 0.2s ease;
    }

    button:hover {
        background-color: #5c258d;
    }

    button:active {
        transform: scale(0.95);
    }
</style>


<div class="todo-app">
    <div class="header">TODO</div>
    <div class="input-container">
        <input type="text" bind:value={newTask} placeholder="Create a new todo..." on:keyup="{event => event.key === 'Enter' && addTask()}" />
        <button on:click={addTask}>Add</button>
    </div>
    <ul class="todo-list">
        {#each filterTasks() as task, index}
            <li class="todo-item">
                <span class:completed={task.completed} on:click={() => toggleCompletion(index)}>{task.text}</span>
                <button on:click={() => toggleCompletion(index)}>{task.completed ? 'Undo' : '✓'}</button>
            </li>
        {/each}
    </ul>
    <div class="footer">
        <span>{activeTasksCount} items left</span>
        <div>
            <span class="filter-btn" on:click={() => filter = 'all'}>All</span> |
            <span class="filter-btn" on:click={() => filter = 'active'}>Active</span> |
            <span class="filter-btn" on:click={() => filter = 'completed'}>Completed</span>
        </div>
    </div>
</div>

