# Fast Zero

API REST para gerenciamento de usuários, desenvolvida com FastAPI, banco de dados assíncrono e autenticação JWT.

## Tecnologias

- Python 3.13
- FastAPI / Uvicorn
- SQLAlchemy assíncrono + SQLite (aiosqlite)
- Alembic
- Pydantic / pydantic-settings
- Pwdlib (hash de senhas) e PyJWT
- Poetry
- Ruff
- Pytest / pytest-cov
- Taskipy

## Como executar

1. Instale as dependências:

```bash
poetry install
```

2. Crie o arquivo `.env` na raiz do projeto:

```env
DATABASE_URL=sqlite+aiosqlite:///database.db
SECRET_KEY=dev-secret-key-change-me-32-bytes-long
ALGORITHM=HS256
ACCESS_TOKEN_EXPIRE_MINUTES=30
```

3. Aplique as migrações do banco:

```bash
poetry run alembic upgrade head
```

4. Inicie o servidor de desenvolvimento:

```bash
poetry run task serve
```

A aplicação estará disponível em:

- http://localhost:8000
- Documentação Swagger: http://localhost:8000/docs
- Documentação ReDoc: http://localhost:8000/redoc

## Como testar

```bash
poetry run task tests
```

O comando executa o lint, os testes com cobertura e gera o relatório HTML em `htmlcov/`.

## Endpoints principais

- `GET /` — mensagem de boas-vindas
- `GET /users/` — lista usuários
- `GET /users/{user_id}` — busca um usuário
- `POST /users/` — cria um usuário
- `PUT /users/{user_id}` — atualiza um usuário (autenticado)
- `DELETE /users/{user_id}` — remove um usuário (autenticado)
- `POST /auth/token` — obtém o token de acesso
- `POST /auth/refresh_token` — renova o token de acesso

## Estrutura

```text
.
├── alembic.ini
├── migrations/
├── src/
│   └── fast_zero/
│       ├── app.py
│       ├── database.py
│       ├── models.py
│       ├── routers/
│       ├── schemas.py
│       ├── security.py
│       └── settings.py
├── tests/
├── pyproject.toml
└── README.md
```
# fast_zeroAnthony
