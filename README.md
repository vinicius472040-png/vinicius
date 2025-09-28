// server.js
const express = require('express');
const app = express();
app.use(express.json());

// Simulando dados
let reservas = [
  { id: 1, nome: 'Produto A', descricao: 'Descrição A' },
  { id: 2, nome: 'Produto B', descricao: 'Descrição B' },
];

let perfil = { nome: 'João', email: 'joao@email.com', senha: '123456' };

// Obter reservas
app.get('/api/reservas', (req, res) => {
  res.json(reservas);
});

// Enviar avaliação
app.post('/api/avaliacoes', (req, res) => {
  const { produtoId, texto } = req.body;
  console.log(`Avaliação recebida para produto ${produtoId}: ${texto}`);
  res.json({ success: true });
});

// Atualizar perfil
app.put('/api/perfil', (req, res) => {
  const { nome, email, senha } = req.body;
  perfil = { nome, email, senha };
  console.log('Perfil atualizado:', perfil);
  res.json({ success: true });
});

app.listen(3000, () => console.log('Servidor rodando na porta 3000'));
