// 1) Variáveis simples + inferência
// O TypeScript consegue inferir o tipo das variáveis com base no valor atribuído.
// Aqui, 'nomeAluno' é uma string, 'nota1' e 'nota2' são números, e 'aprovado' é um booleano.
const nomeAluno = 'Ana';   // nomeAluno é uma string
let nota1 = 8.5;           // nota1 é um número
let nota2 = 7;             // nota2 é um número
let aprovado = true;       // aprovado é um booleano
console.log('1) Variáveis:', { nomeAluno, nota1, nota2, aprovado });

// 2) Tipos explícitos + função tipada (média)
// Aqui definimos uma função 'media' que recebe dois números e retorna a média entre eles.
// A função também tem seu tipo de retorno explícito como 'number', garantindo que sempre retornará um número.
function media(a: number, b: number): number {
  return Number(((a + b) / 2).toFixed(2));  // Retorna a média arredondada para 2 casas decimais.
}
const mediaAna = media(nota1, nota2);  // Calcula a média de 'nota1' e 'nota2'
console.log('2) Média de Ana:', mediaAna);

// 3) Array tipado + map/filter
// Definimos um array tipado de números ('notas') e aplicamos métodos como 'filter' e 'map'.
// 'filter' retorna apenas as notas maiores ou iguais a 8.
// 'map' ajusta todas as notas, aumentando 0.5 (mas nunca acima de 10).
const notas: number[] = [6, 7.5, 8, 9.2, 10];  // Array de notas, todas do tipo número.
const acimaDe8 = notas.filter(n => n >= 8);  // Filtra notas maiores ou iguais a 8.
const mediasAjustadas = notas.map(n => Math.min(n + 0.5, 10));  // Ajusta as notas, aumentando 0.5, mas limita a 10.
console.log('3) Arrays:', { acimaDe8, mediasAjustadas });

// 4) Tupla (nome, média) + ordenação
// Uma tupla é como um array, mas com tipos definidos e quantidade fixa de elementos.
// Aqui, estamos criando uma tupla para registrar o nome de um aluno e sua média.
const registro: [string, number] = ['Edu', media(9, 8.5)];  // Tupla contendo nome (string) e média (número)
console.log('4) Tupla (nome, média):', registro);

// 5) Type/Interface + lista de alunos
// Criamos um tipo 'Aluno' que é um objeto contendo um ID, nome e uma lista de notas.
// Usamos esse tipo para criar uma lista de alunos, onde cada aluno tem um conjunto de notas.
// A função 'mediaAluno' calcula a média das notas de um aluno.
type Aluno = { id: string; nome: string; notas: number[] };  // Define o tipo Aluno
const alunos: Aluno[] = [  // Cria uma lista de alunos com seus dados
  { id: 'a1', nome: 'Ana',  notas: [8, 7.5, 9] },
  { id: 'a2', nome: 'Bia',  notas: [6, 6.5, 7] },
  { id: 'a3', nome: 'Cris', notas: [9.5, 8.5, 10] },
];

function mediaAluno(a: Aluno): number {  // Função para calcular a média de um aluno
  const soma = a.notas.reduce((acc, n) => acc + n, 0);  // Soma todas as notas
  return Number((soma / a.notas.length).toFixed(2));  // Calcula a média e arredonda para 2 casas decimais
}
console.log('5) Médias:', alunos.map(a => ({ nome: a.nome, media: mediaAluno(a) })));

// 6) União de tipos + narrowing
// Aqui, usamos um tipo união para permitir que a variável 'id' seja tanto um número quanto uma string.
// A função 'formatarId' verifica o tipo de 'id' e formata de acordo (número com 3 dígitos ou string em maiúsculo).
type Id = number | string;  // O tipo 'Id' pode ser tanto número quanto string
function formatarId(id: Id): string {
  return typeof id === 'number' ? id.toString().padStart(3, '0') : id.toUpperCase();  // Formatação baseada no tipo
}
console.log('6) União:', formatarId(7), formatarId('a3'));

// 7) Enum de status + classificação por média
// Usamos um 'enum' para representar os possíveis status de um aluno (aprovado, recuperação ou reprovado).
// A função 'statusPorMedia' usa a média do aluno para determinar seu status.
enum StatusAluno { Aprovado = 'APROVADO', Recuperacao = 'RECUPERAÇÃO', Reprovado = 'REPROVADO' }  // Define o enum
function statusPorMedia(m: number): StatusAluno {
  if (m >= 7) return StatusAluno.Aprovado;  // Aprovado se a média for maior ou igual a 7
  if (m >= 5) return StatusAluno.Recuperacao;  // Recuperação se a média for entre 5 e 7
  return StatusAluno.Reprovado;  // Reprovado se a média for abaixo de 5
}
console.log('7) Status:', alunos.map(a => ({ nome: a.nome, status: statusPorMedia(mediaAluno(a)) })));

// 8) Map<string, number> (nome → média)
// Aqui, usamos um 'Map' para associar o nome de cada aluno à sua média.
// O 'Map' permite armazenar pares chave-valor, e a chave é o nome do aluno enquanto o valor é a média calculada.
const mediasPorNome = new Map<string, number>();  // Cria um novo mapa onde a chave é o nome (string) e o valor é a média (número)
for (const a of alunos) mediasPorNome.set(a.nome, mediaAluno(a));  // Adiciona cada aluno ao mapa
console.log('8) Map (nome→média):', Array.from(mediasPorNome.entries()));  // Exibe o mapa como um array de pares chave-valor

export {};  // O 'export {}' garante que o arquivo seja tratado como um módulo, evitando erros de escopo.
