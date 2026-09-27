<div align="center">

# CineSenai

Front-end de um sistema de cinema — catálogo de filmes, sessões, reserva de assentos e painel administrativo — construído em **React**.

![React](https://img.shields.io/badge/React-19-61DAFB?style=flat-square&logo=react&logoColor=black)
![Vite](https://img.shields.io/badge/Vite-6-646CFF?style=flat-square&logo=vite&logoColor=white)
![React Router](https://img.shields.io/badge/React%20Router-7-CA4245?style=flat-square&logo=reactrouter&logoColor=white)
![Deploy](https://img.shields.io/badge/Deploy-Vercel-000000?style=flat-square&logo=vercel&logoColor=white)

[**🔗 Aplicação publicada**](#) · [**⚙️ Repositório da API**](#)

</div>

---

## Sobre este projeto

Esta é a tela do CineSenai: a parte que a pessoa usa no navegador para ver o catálogo de filmes, escolher uma sessão, reservar assento e acompanhar suas reservas. Administradores também gerenciam filmes, salas, sessões e reservas por aqui. O front-end não guarda nenhum dado sozinho — toda informação é enviada e buscada de uma API própria, publicada separadamente.

A API que esse front-end consome é um projeto à parte, feito em Java com Spring Boot ([link do repositório](#)).

## Funcionalidades

- Catálogo de filmes em cartaz, com detalhes de cada um
- Lista de sessões disponíveis por filme
- Reserva de assento com mapa visual da sala (assentos ocupados destacados)
- Tela de "Minhas reservas", com opção de cancelar
- Cadastro e login de usuário
- Painel administrativo (acesso restrito): gestão de filmes, salas, sessões, reservas e usuários

## Tecnologias usadas

| Item | Tecnologia |
|---|---|
| Biblioteca | React |
| Build tool | Vite |
| Navegação entre páginas | React Router |
| Publicação | Vercel |

## Como a comunicação com a API funciona

O endereço da API não fica fixo no código: ele vem de uma variável de ambiente (`VITE_API_URL`), configurada na própria Vercel. Isso permite trocar de API (por exemplo, para testar localmente ou apontar para outro ambiente) sem precisar alterar nenhum arquivo do projeto.

Depois do login, a aplicação guarda um token de acesso (JWT) e passa a enviá-lo automaticamente em cada ação seguinte, provando para a API quem é o usuário logado — inclusive para liberar as telas do painel administrativo apenas para quem tem esse papel.

## Deploy

Publicado na **Vercel**, que builda o projeto automaticamente a cada atualização enviada para o repositório.
