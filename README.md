# Lista_Tarefas

<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title> Lista de Tarefa</title>
    <link rel="stylesheet" href="./style.css">
</head>
<body>
    <div class="container">
        <div class="header">
        
            <img src="Captura de tela 2025-04-01 164533.png" alt="icone lista de tarefas">
            <h1>Lista de Tarefas</h1>
        </div>
        <input type="text" id="tarefaInput" placeholder="Digite uma tarefa">
        <button class="adicionarTarefa" onclick="adicionarTarefa()">Adicionar</button>
        <ul id="listaTarefas"></ul>
    </div>
    
    <script>
        let tarefas = [];

        function adicionarTarefa(){
            const input = document.getElementById('tarefaInput')
            const tarefa = input.value.trim();

            if(tarefas){
                tarefas.push(tarefa);
                input.value = '';
                atualizarLista();
            }
        }

        function removerTarefa(index){
            tarefas.splice(index, 1);
            atualizarLista();
        }

        function atualizarLista(){
            const lista= document.getElementById('listaTarefas');
            lista.innerHTML = '';
            tarefas.forEach((tarefa, index) => {
                const li = document.createElement('li');
                li.innerHTML = `${tarefa} <button class = "removerTarefa" onclick="removerTarefa(${index})">Remover</button>`

                lista.appendChild(li);
            });
        }
    </script>
</body>
</html>

body{
    font-family: Arial, Helvetica, sans-serif;
    text-align: center;
    margin: 50px;
}

.container{
    max-width: 400px;
    margin: auto;
    padding: 20px;
    border: 2px solid #333;
    border-radius: 10px;
}

ul{
    list-style-type: none;
    padding: 0;
}

li{
    padding: 5px;
    border-bottom: 1px solid #ddd;
    justify-content: space-between; /* Garante que a tarefa e o botão estejam nas extremidades*/
    align-items: center;
}

input, button{
    margin: 10px;
    padding: 10px;
    font-size: 16px;
    cursor: pointer;
    border-radius: 10px;
}

.adicionarTarefa{
    background-color: rgb(69, 173, 69);
    color: #fff;
}

.removerTarefa{
    margin-left: 20px;
    background-color: rgb(229, 53, 53);
    color: #fff;
}

.header{
    display: flex;
    align-items: center;
    justify-content: center;
}

.header img{
    width: 40px;
    margin-right: 10px;
}
