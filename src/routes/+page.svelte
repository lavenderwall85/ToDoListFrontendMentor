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
</style>

<div class="todo-app">
    <div class="header">TODO</div>
    <div class="input-container">
        <input type="text" placeholder="Create a new todo..." />
    </div>
    <ul class="todo-list">
        <li class="todo-item">
            <span>Example Task</span>
            <button>✓</button>
        </li>
        <li class="todo-item">
            <span>Another Task</span>
            <button>✓</button>
        </li>
    </ul>
    <div class="footer">
        <span>3 items left</span>
        <span>All | Active | Completed</span>
    </div>
</div>



