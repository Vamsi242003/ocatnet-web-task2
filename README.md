//html 

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>To-Do List</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body >
    <div class="container">
        <h1>To-Do List</h1>
        <input type="text" id="new-task" placeholder="Add a new task">
        <button id="add-task-btn">Add Task</button>
        <ul id="task-list"></ul>
    </div>
    <script src="script.js"></script>
</body>
</html>


//css


body {
    font-family: Arial, sans-serif;
    background-color: green;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: 0;
}

.container {
    background: yellow;
    padding: 20px;
    border-radius: 5px;
    width: 300px;
    text-align: center;
}

#new-task {
    width: calc(100% - 20px);
    padding: 10px;
    margin: 10px 0;
    border: 1px solid black;
    border-radius: 3px;
}

button {
    padding: 10px 20px;
    background: green;
    color: white;
    border: none;
    border-radius: 3px;
    cursor: pointer;
}

button:hover {
    background:black;
}

ul {
    list-style-type: none;
    padding: 0;
}

li {
    background: none;
    padding: 10px;
    margin: 5px 0;
    border-radius: 3px;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

li.completed {
    text-decoration: line-through;
    color: gray;
}


//js

document.addEventListener('DOMContentLoaded', () => {
    const taskInput = document.getElementById('new-task');
    const addTaskBtn = document.getElementById('add-task-btn');
    const taskList = document.getElementById('task-list');

    function addTask() {
        const taskText = taskInput.value.trim();
        if (taskText !== '') {
            const li = document.createElement('li');
            li.textContent = taskText;
            li.addEventListener('click', () => {
                li.classList.toggle('completed');
            });
            const removeBtn = document.createElement('button');
            removeBtn.textContent = 'Remove';
            removeBtn.addEventListener('click', () => {
                taskList.removeChild(li);
            });
            li.appendChild(removeBtn);
            taskList.appendChild(li);
            taskInput.value = '';
        }
    }

    addTaskBtn.addEventListener('click', addTask);
    taskInput.addEventListener('keypress', (e) => {
        if (e.key === 'Enter') {
            addTask();
        }
    });
});
