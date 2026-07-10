# 🎬 CineSenai — Front-end (CineSenai-Final)

Front-end em **React + Vite** de um sistema de cinema: catálogo de filmes, sessões, reserva de assentos e um painel administrativo. Consome a API **SpringBootAPI-Cinema**.

---

## 🛠 Tecnologias

- React 19
- React Router 7
- Vite 6
- CSS puro (sem framework de UI)

---

## ▶️ Como rodar

### Pré-requisitos
- Node.js 18+
- O back-end (**SpringBootAPI-Cinema**) rodando em `http://localhost:8080`

### 1. Instalar dependências
```bash
npm install
```

### 2. Rodar em modo desenvolvimento
```bash
npm run dev
```
A aplicação sobe em `http://localhost:3000`.

O Vite já está configurado (`vite.config.js`) para redirecionar automaticamente ao back-end:
- `/api/**` → `http://localhost:8080`
- `/uploads/**` → `http://localhost:8080` (necessário para os pôsteres de filme carregarem)

### 3. Build de produção
```bash
npm run build
```
Os arquivos ficam em `dist/`. Para servir esse build, lembre-se de configurar um proxy equivalente ao do Vite (`/api` e `/uploads` apontando para o back-end) no seu servidor/hospedagem.

---

## 🔐 Login

Use o usuário administrador criado automaticamente pelo back-end na primeira execução:
- **E-mail:** `admin@cinemasenai.com`
- **Senha:** `Admin@134`

Ou cadastre um novo usuário comum pela própria tela de cadastro.

---

## 🚀 Funcionalidades

**Área pública / usuário logado**
- Catálogo de filmes em cartaz
- Detalhes do filme e sessões disponíveis
- Reserva de assentos com mapa visual (livre / selecionado / ocupado)
- Histórico de reservas (com cancelamento)
- Cadastro e login

**Área administrativa** (`/admin/*`, requer cargo `ADMIN`)
- Dashboard com relatório de receita e ranking de filmes mais reservados
- Gerenciar filmes (criar, editar, excluir, upload de pôster)
- Gerenciar salas (nome, fileiras, assentos por fileira)
- Gerenciar sessões (agendar filme + sala + horário + preço)
- Ver todas as reservas do sistema
- Promover um usuário para ADMIN a partir do UUID dele

---

## 📂 Estrutura do projeto

```
src
├── components      # componentes reutilizáveis (ex.: ProtectedRoute)
├── context          # AuthContext (sessão/token) e ToastContext (notificações)
├── pages            # telas da aplicação
│   └── admin        # telas do painel administrativo
├── services
│   └── api.js       # camada única de acesso à API (fetch + tratamento de erros)
├── App.jsx          # definição das rotas
└── main.jsx         # ponto de entrada
```

---

## 🔑 Autenticação

O token JWT retornado no login/cadastro é salvo no `localStorage` (`token` e `user`) e enviado em todas as chamadas autenticadas via header `Authorization: Bearer <token>` (ver `services/api.js`).

- Uma resposta **401** (token inválido/expirado) desloga o usuário automaticamente.
- Uma resposta **403** (usuário autenticado mas sem permissão para aquela ação) **não** desloga — apenas exibe um erro, já que não significa sessão inválida.

Rotas administrativas no front (`/admin/*`) são protegidas por `ProtectedRoute`, que redireciona para `/login` (sem sessão) ou para `/` (sessão sem cargo `ADMIN`).

---

## ⚠️ Pontos de atenção conhecidos

- Não há paginação nas listagens (filmes, sessões, reservas); em uma base de dados grande isso deve ser adicionado tanto aqui quanto na API.
- A promoção de usuário a admin exige colar o UUID manualmente — não há uma tela de busca/listagem de usuários no painel.
