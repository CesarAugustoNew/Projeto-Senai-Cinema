<div align="center">

# CineSenai

Front-end de um sistema de cinema — catálogo de filmes, sessões, reserva de assentos e painel administrativo — construído em **React**.

![React](https://img.shields.io/badge/React-19-61DAFB?style=flat-square&logo=react&logoColor=black)
![Vite](https://img.shields.io/badge/Vite-6-646CFF?style=flat-square&logo=vite&logoColor=white)
![React Router](https://img.shields.io/badge/React%20Router-7-CA4245?style=flat-square&logo=reactrouter&logoColor=white)
![Deploy](https://img.shields.io/badge/Deploy-Vercel-000000?style=flat-square&logo=vercel&logoColor=white)

[**🔗 Aplicação publicada**](https://projeto-senai-cinema.vercel.app/) · [**⚙️ Repositório da API**](https://github.com/CesarAugustoNew/SpringBootAPI-Cinema)

</div>

---

## Sobre este projeto

Esta é a tela do CineSenai: a parte que a pessoa usa no navegador para ver o catálogo de filmes, escolher uma sessão, reservar assento e acompanhar suas reservas. Administradores também gerenciam filmes, salas, sessões e reservas por aqui. O front-end não guarda nenhum dado sozinho — toda informação é enviada e buscada de uma API própria, publicada separadamente.

A API que esse front-end consome é um projeto à parte, feito em Java com Spring Boot ([link do repositório](#)).

## Demonstração
<img width="1913" height="954" alt="cadastro" src="https://github.com/user-attachments/assets/dbda9daa-372e-4d76-92b4-76c52f3a6192" />
<br>
<br>
<img width="1918" height="949" alt="login" src="https://github.com/user-attachments/assets/c5d359b5-6cb8-4410-adc4-761709eb2acc" />
<br>
<br>
<img width="1915" height="944" alt="catalogofilmes" src="https://github.com/user-attachments/assets/d44a6501-b545-4e57-851e-1b418f5414c9" />
<br>
<br>
<img width="1916" height="952" alt="filmeselecionado" src="https://github.com/user-attachments/assets/2ff5f30a-e073-4cd4-ade7-c3d70de587d3" />
<br>
<br>
<img width="1916" height="952" alt="compra" src="https://github.com/user-attachments/assets/6faf0683-e8b3-4f57-bfe7-11dec84a570d" />
<br>
<br>
<img width="1911" height="933" alt="minhasreservas" src="https://github.com/user-attachments/assets/4d360817-5981-4dba-8c42-83d803e44be7" />
<br>
<br>
<img width="1917" height="946" alt="salascriadas" src="https://github.com/user-attachments/assets/ec346ae4-41fe-4147-934f-d1a3f427e0d5" />
<br>
<br>
<img width="1915" height="946" alt="sessoes" src="https://github.com/user-attachments/assets/bafa2619-7508-4e3c-861f-86b97b7eb61e" />
<br>
<br>
<img width="1908" height="941" alt="painel" src="https://github.com/user-attachments/assets/ed202b90-76c1-4588-b549-2f5224150b8f" />


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
