# 🎬 CineSenai — Front-end (CineSenai-Final)

Front-end em **React + Vite** de um sistema de cinema: catálogo de filmes, sessões, reserva de assentos e um painel administrativo. Consome a API **SpringBootAPI-Cinema**.

---

<img width="1920" height="925" alt="catalogo1" src="https://github.com/user-attachments/assets/b25b2329-f9b2-4c3d-bd41-224d32090055" />
<img width="1917" height="854" alt="catalogo2" src="https://github.com/user-attachments/assets/540bce65-6151-4342-a9a8-13cadf09724a" />
<br><br>
<img width="1912" height="923" alt="Filmes" src="https://github.com/user-attachments/assets/95694602-2d50-4d09-b71a-a0ef5a77aa4e" />
<br><br>
<img width="1920" height="919" alt="Sala" src="https://github.com/user-attachments/assets/fc4974d3-0adf-427d-8ead-8585509b8fc3" />
<br><br>
<img width="1922" height="913" alt="sessoes" src="https://github.com/user-attachments/assets/8e4d4379-16c3-4346-ad98-0081939de814" />
<br><br>
<img width="1917" height="914" alt="reservas" src="https://github.com/user-attachments/assets/488ecb87-2499-473e-99db-380faa8cd22a" />
<br><br> 
<img width="1918" height="920" alt="minhas reservas" src="https://github.com/user-attachments/assets/dbbfd995-8a76-4a53-bb90-d31aa6063947" />
<br><br> 
<img width="1908" height="1059" alt="image" src="https://github.com/user-attachments/assets/2c310a80-ab38-4664-bcfe-0c3ff4ce95f4" />
<br><br>
<img width="1920" height="911" alt="paineladm" src="https://github.com/user-attachments/assets/9966b33e-8da4-448c-9449-032f85a71ea7" />

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











