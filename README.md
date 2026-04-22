# Array

q1

<input id="itemInput" placeholder="Digite um item">
<button onclick="adicionar()">Adicionar</button>

<ul id="lista"></ul>

<script>
let itens = [];

function adicionar() {
  let valor = document.getElementById("itemInput").value;
  itens.push(valor);
  atualizar();
}

function remover(index) {
  itens.splice(index, 1);
  atualizar();
}

function atualizar() {
  let ul = document.getElementById("lista");
  ul.innerHTML = "";

  itens.forEach((item, i) => {
    ul.innerHTML += `<li>${item} <button onclick="remover(${i})">Remover</button></li>`;
  });
}
</script>

q2

<input id="nome" placeholder="Nome">
<input id="nota" type="number" placeholder="Nota">
<button onclick="adicionar()">Adicionar</button>
<button onclick="filtrar()">Aprovados</button>

<ul id="lista"></ul>

<script>
let alunos = [];

function adicionar() {
  let nome = document.getElementById("nome").value;
  let nota = Number(document.getElementById("nota").value);

  alunos.push({ nome, nota });
  mostrar(alunos);
}

function mostrar(lista) {
  let ul = document.getElementById("lista");
  ul.innerHTML = "";

  lista.forEach(a => {
    ul.innerHTML += `<li>${a.nome} - ${a.nota}</li>`;
  });
}

function filtrar() {
  let aprovados = alunos.filter(a => a.nota >= 7);
  mostrar(aprovados);
}
</script>

q3

<input id="titulo" placeholder="Tarefa">
<select id="prioridade">
  <option value="normal">Normal</option>
  <option value="alta">Alta</option>
</select>

<button onclick="adicionar()">Adicionar</button>

<ul id="lista"></ul>

<script>
let tarefas = [];

function adicionar() {
  let titulo = document.getElementById("titulo").value;
  let prioridade = document.getElementById("prioridade").value;

  let tarefa = { titulo, prioridade };

  if (prioridade === "alta") {
    tarefas.unshift(tarefa);
  } else {
    tarefas.push(tarefa);
  }

  atualizar();
}

function atualizar() {
  let ul = document.getElementById("lista");
  ul.innerHTML = "";

  tarefas.forEach(t => {
    ul.innerHTML += `<li>${t.titulo} (${t.prioridade})</li>`;
  });
}
</script>

q4

<ul id="lista"></ul>

<script>
const produtos = [
  { nome: "Mouse", preco: 50 },
  { nome: "Teclado", preco: 100 },
  { nome: "Monitor", preco: 800 }
];

const comDesconto = produtos.map(p => ({
  nome: p.nome,
  preco: p.preco * 0.9
}));

let ul = document.getElementById("lista");

comDesconto.forEach(p => {
  ul.innerHTML += `<li>${p.nome} - R$ ${p.preco.toFixed(2)}</li>`;
});
</script>

q5

<button onclick="adicionar()">Adicionar produto</button>
<button onclick="remover()">Remover último</button>

<ul id="lista"></ul>

<script>
let carrinho = [];

function adicionar() {
  carrinho.push({ nome: "Produto " + (carrinho.length + 1) });
  atualizar();
}

function remover() {
  carrinho.pop();
  atualizar();
}

function atualizar() {
  let ul = document.getElementById("lista");
  ul.innerHTML = "";

  carrinho.forEach(p => {
    ul.innerHTML += `<li>${p.nome}</li>`;
  });
}
</script>


q6

<button onclick="mostrarTodos()">Todos</button>
<button onclick="maiores()">Maiores de 18</button>

<ul id="lista"></ul>

<script>
let usuarios = [
  { nome: "Ana", idade: 17 },
  { nome: "João", idade: 20 },
  { nome: "Carlos", idade: 15 }
];

function mostrar(lista) {
  let ul = document.getElementById("lista");
  ul.innerHTML = "";

  lista.forEach(u => {
    ul.innerHTML += `<li>${u.nome} - ${u.idade}</li>`;
  });
}

function mostrarTodos() {
  mostrar(usuarios);
}

function maiores() {
  let filtrados = usuarios.filter(u => u.idade >= 18);
  mostrar(filtrados);
}

mostrarTodos();
</script>

q7

<input id="tarefa">
<button onclick="adicionar()">Adicionar</button>

<ul id="lista"></ul>

<script>
let tarefas = JSON.parse(localStorage.getItem("tarefas")) || [];

function salvar() {
  localStorage.setItem("tarefas", JSON.stringify(tarefas));
}

function adicionar() {
  let t = document.getElementById("tarefa").value;
  tarefas.push(t);
  salvar();
  atualizar();
}

function atualizar() {
  let ul = document.getElementById("lista");
  ul.innerHTML = "";

  tarefas.forEach(t => {
    ul.innerHTML += `<li>${t}</li>`;
  });
}

atualizar();
</script>

q8

<input id="tarefa">
<button onclick="adicionar()">Adicionar</button>

<ul id="lista"></ul>

<script>
let tarefas = [];

function adicionar() {
  let t = document.getElementById("tarefa").value;
  tarefas.push(t);
  atualizar();
}

function editar(i) {
  let novo = prompt("Novo valor:");
  tarefas.splice(i, 1, novo);
  atualizar();
}

function atualizar() {
  let ul = document.getElementById("lista");
  ul.innerHTML = "";

  tarefas.forEach((t, i) => {
    ul.innerHTML += `<li>${t} <button onclick="editar(${i})">Editar</button></li>`;
  });
}
</script>

q9

<input id="titulo">
<input id="genero">
<input id="ano">
<button onclick="adicionar()">Adicionar</button>
<button onclick="filtrar()">Filtrar por gênero</button>

<ul id="lista"></ul>

<script>
let filmes = [];

function adicionar() {
  let titulo = document.getElementById("titulo").value;
  let genero = document.getElementById("genero").value;
  let ano = document.getElementById("ano").value;

  filmes.push({ titulo, genero, ano });
  mostrar(filmes);
}

function mostrar(lista) {
  let ul = document.getElementById("lista");
  ul.innerHTML = "";

  lista.forEach(f => {
    ul.innerHTML += `<li>${f.titulo} - ${f.genero} (${f.ano})</li>`;
  });
}

function filtrar() {
  let g = prompt("Digite o gênero:");
  let filtrados = filmes.filter(f => f.genero === g);
  mostrar(filtrados);
}
</script>

q10

<input id="nome">
<input id="pontos" type="number">
<button onclick="adicionar()">Adicionar</button>

<ul id="lista"></ul>

<script>
let jogadores = [];

function adicionar() {
  let nome = document.getElementById("nome").value;
  let pontos = Number(document.getElementById("pontos").value);

  jogadores.push({ jogador: nome, pontos });
  atualizar();
}

function atualizar() {
  let ranking = jogadores
    .sort((a, b) => b.pontos - a.pontos)
    .map((j, i) => `${i + 1}º ${j.jogador} - ${j.pontos} pontos`);

  let ul = document.getElementById("lista");
  ul.innerHTML = "";

  ranking.forEach(r => {
    ul.innerHTML += `<li>${r}</li>`;
  });
}
</script>
