# Test Clinic Backend API 💊

**Descrição**

API construída em Laravel para gerenciar usuários, pacientes e históricos clínicos — inclui endpoints protegidos por JWT para operações autenticadas.

---

## 🧰 Tecnologias

- PHP (recomenda-se >= 8.0)
- Laravel
- Composer
- MySQL / MariaDB (ou outro DB configurado em `.env`)
- Docker / docker-compose (opcional)
- jwt-auth (middleware `jwt.auth`)

---

## ✅ Pré-requisitos

- Git
- PHP
- Composer
- Banco de dados (MySQL)

---

## 🚀 Instalação

1. Clone o repositório:

   ```bash
   git clone <repo-url>
   cd Test-clinic-backend-api
   ```

2. Instale dependências:

   ```bash
   composer install
   ```

3. Copie o `.env` e ajuste variáveis (DB, APP_URL, etc.):

   ```bash
   cp .env.example .env
   ```

4. Gere a chave da aplicação e a chave JWT:

   ```bash
   php artisan key:generate
   php artisan jwt:secret
   ```

5. Rode migrations e seeders:

   ```bash
   php artisan migrate --seed
   ```

---

## ▶️ Execução local

```bash
php artisan serve --host=0.0.0.0 --port=8000
```

A API ficará disponível em `http://localhost:8000` (ou conforme `APP_URL`).

---


## 🔐 Autenticação

As rotas protegidas exigem o header:

```
Authorization: Bearer <token>
```

Para obter o token, use o endpoint de login (ex.: `POST /api/user/login`).

Exemplo de login com cURL:

```bash
curl -X POST http://localhost:8000/api/user/login \
  -H "Content-Type: application/json" \
  -d '{"email": "user@example.com", "password": "secret"}'
```

---

## 📚 Rotas

- POST `/api/user/login` — autenticação (retorna token)

Rotas protegidas por `jwt.auth`:

- `GET /api/user/info`
- `POST /api/user/register`
- `POST /api/user/logout`

Pacientes `/api/patient`:

- `GET /api/patient/patients`
- `GET /api/patient/info/{id}`
- `POST /api/patient/register`
- `PUT /api/patient/update/{id}`
- `DELETE /api/patient/delete/{id}`

Históricos de pacientes `/api/patient`:

- `GET /api/patient/histories`
- `GET /api/patient/history/info/{id}`
- `POST /api/patient/history/register`
- `PUT /api/patient/history/update/{id}`
- `DELETE /api/patient/history/{id}`

Outras:

- `GET /api/specialties`
- `GET /api/regionals`

---

## 📝 Observações

- Ajuste variáveis de ambiente em `.env` (DB, MAIL, JWT_SECRET, etc.).
- Verifique se o middleware `jwt.auth` está configurado corretamente (dependência `tymon/jwt-auth` ou similar).

---