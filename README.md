<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Lista de Tarefas</title>

  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: Arial, sans-serif;
    }

    body {
      background: #f4f4f4;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
    }

    .container {
      background: white;
      width: 400px;
      padding: 25px;
      border-radius: 12px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.15);
    }

    h1 {
      text-align: center;
      margin-bottom: 20px;
      color: #333;
    }

    .input-area {
      display: flex;
      gap: 10px;
      margin-bottom: 20px;
    }

    input {
      flex: 1;
      padding: 10px;
      border: 2px solid #ddd;
      border-radius: 8px;
      outline: none;
    }

    button {
      padding: 10px 15px;
      border: none;
      background: #4CAF50;
      color: white;
      border-radius: 8px;
      cursor: pointer;
      transition: 0.3s;
    }

    button:hover {
      background: #45a049;
    }

    ul {
      list-style: none;
    }

    li {
      background: #f9f9f9;
      padding: 12px;
      margin-bottom: 10px;
      border-radius: 8px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      transition: 0.3s;
    }

    li.completed {
      text-decoration: line-through;
      color: gray;
      background: #e0e0e0;
    }

    .actions {
      display: flex;
      gap: 8px;
    }

    .complete-btn {
      background: #2196F3;
    }

    .complete-btn:hover {
      background: #1976D2;
    }

    .delete-btn {
      background: #f44336;
    }

    .delete-btn:hover {
      background: #d32f2f;
    }
  </style>
</head>
<body>

  <div class="container">
    <h1>📝 Lista de Tarefas</h1>

    <div class="input-area">
      <input type="text" id="taskInput" placeholder="Digite uma tarefa...">
      <button onclick="addTask()">Adicionar</button>
    </div>

    <ul id="taskList"></ul>
  </div>

  <script>
    function addTask() {
      const input = document.getElementById("taskInput");
      const taskText = input.value.trim();

      if (taskText === "") {
        alert("Digite uma tarefa!");
        return;
      }

      const li = document.createElement("li");

      li.innerHTML = `
        <span>${taskText}</span>

        <div class="actions">
          <button class="complete-btn" onclick="toggleComplete(this)">
            ✔
          </button>

          <button class="delete-btn" onclick="deleteTask(this)">
            ✖
          </button>
        </div>
      `;

      document.getElementById("taskList").appendChild(li);

      input.value = "";
    }

    function toggleComplete(button) {
      const li = button.parentElement.parentElement;
      li.classList.toggle("completed");
    }

    function deleteTask(button) {
      const li = button.parentElement.parentElement;
      li.remove();
    }

    // Adicionar tarefa apertando Enter
    document.getElementById("taskInput").addEventListener("keypress", function(e) {
      if (e.key === "Enter") {
        addTask();
      }
    });
  </script>

</body>
</html>
