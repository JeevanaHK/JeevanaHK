<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Task Management System</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            margin: 0;
            padding: 0;
        }

        header {
            background-color: #333;
            color: #fff;
            text-align: center;
            padding: 1em;
        }

        main {
            max-width: 600px;
            margin: 20px auto;
            padding: 20px;
            background-color: #fff;
            border-radius: 5px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }

        h2 {
            color: #333;
        }

        ul {
            list-style: none;
            padding: 0;
        }

        li {
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 1px solid #eee;
            padding: 10px 0;
        }

        .task-actions {
            display: flex;
        }

        button {
            background-color: #333;
            color: #fff;
            border: none;
            padding: 5px 10px;
            cursor: pointer;
            margin-left: 5px;
        }

        input[type="text"] {
            width: 70%;
            padding: 8px;
            margin-right: 5px;
        }

        input[type="submit"] {
            background-color: #333;
            color: #fff;
            border: none;
            padding: 8px 15px;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <header>
        <h1>Task Management System</h1>
    </header>
    <main>
        <h2>Add Task</h2>
        <form id="taskForm">
            <input type="text" id="taskInput" placeholder="Enter task...">
            <input type="submit" value="Add Task">
        </form>

        <h2>Task List</h2>
        <ul id="taskList">
            <!-- Task items will be added here dynamically -->
        </ul>
    </main>

    <script>
        document.getElementById("taskForm").addEventListener("submit", function (e) {
            e.preventDefault();
            addTask();
        });

        function addTask() {
            var taskInput = document.getElementById("taskInput");
            var taskList = document.getElementById("taskList");

            if (taskInput.value.trim() !== "") {
                var li = document.createElement("li");
                li.innerHTML = `
                    <span>${taskInput.value}</span>
                    <div class="task-actions">
                        <button onclick="editTask(this)">Edit</button>
                        <button onclick="deleteTask(this)">Delete</button>
                    </div>
                `;
                taskList.appendChild(li);
                taskInput.value = "";
            }
        }

        function editTask(button) {
            var li = button.closest("li");
            var span = li.querySelector("span");
            var newTask = prompt("Edit task:", span.textContent);
            if (newTask !== null) {
                span.textContent = newTask;
            }
        }

        function deleteTask(button) {
            var li = button.closest("li");
            li.remove();
        }
    </script>
</body>
</html>
