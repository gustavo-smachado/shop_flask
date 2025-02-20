# E-commerce API

Uma API RESTful para um sistema de e-commerce construída com Flask, oferecendo funcionalidades de autenticação de usuários, gerenciamento de produtos e carrinho de compras.

## Visão Geral

Este projeto implementa uma API para uma plataforma de e-commerce com as seguintes funcionalidades principais:
- Autenticação de usuários (login/logout)
- Gerenciamento de produtos (CRUD)
- Gerenciamento de carrinho de compras
- Checkout

A API utiliza SQLite como banco de dados e implementa controle de acesso baseado em sessões.

## Tecnologias Utilizadas

- Python 3.x
- Flask 2.3.0
- Flask-SQLAlchemy 3.1.1
- Flask-Login 0.6.2
- Flask-Cors 3.0.10
- Werkzeug 2.3.0

## Pré-requisitos

- Python 3.x instalado
- pip (gerenciador de pacotes Python)

## Instalação

1. Clone o repositório:
```bash
git clone <URL_DO_REPOSITORIO>
cd <NOME_DO_DIRETORIO>
```

2. Crie um ambiente virtual:
```bash
python -m venv venv
```

3. Ative o ambiente virtual:
- Windows:
```bash
venv\Scripts\activate
```
- Linux/Mac:
```bash
source venv/bin/activate
```

4. Instale as dependências:
```bash
pip install -r requirements.txt
```

5. Crie a pasta `instance` e o banco de dados:
```python
from app import app, db
import os
if not os.path.exists('instance'):
    os.makedirs('instance')
with app.app_context():
    db.create_all()
```

## Executando a Aplicação

Para iniciar o servidor de desenvolvimento:
```bash
python app.py
```

A API estará disponível em `http://127.0.0.1:5000`.

## Endpoints da API

### Autenticação
- `POST /login` - Faz login do usuário
- `POST /logout` - Faz logout do usuário (requer autenticação)

### Produtos
- `GET /api/products` - Lista todos os produtos
- `GET /api/products/<product_id>` - Detalhes de um produto específico
- `POST /api/products/add` - Adiciona um novo produto (requer autenticação)
- `PUT /api/products/update/<product_id>` - Atualiza um produto (requer autenticação)
- `DELETE /api/products/delete/<product_id>` - Deleta um produto (requer autenticação)

### Carrinho
- `POST /api/cart/add/<product_id>` - Adiciona item ao carrinho (requer autenticação)
- `DELETE /api/cart/remove/<product_id>` - Remove item do carrinho (requer autenticação)
- `GET /api/cart` - Visualiza itens do carrinho (requer autenticação)
- `POST /api/cart/checkout` - Finaliza a compra (requer autenticação)

Consulte o arquivo Swagger (`swagger.yaml`) para detalhes completos da API, incluindo parâmetros e respostas.

## Estrutura do Projeto

```
project/
├── app.py           # Código principal da aplicação
├── instance/        # Pasta para arquivos sensíveis
│   └── ecommerce.db # Banco de dados SQLite (gerado após inicialização)
├── requirements.txt # Dependências do projeto
└── swagger.yaml     # Documentação da API
```

## Modelos do Banco de Dados

- **User**: Armazena informações dos usuários (id, username, password)
- **Product**: Armazena produtos (id, name, price, description)
- **CartItem**: Relaciona usuários e produtos no carrinho (id, user_id, product_id)

## Exemplos de Uso

### Login
```bash
curl -X POST http://127.0.0.1:5000/login \
-H "Content-Type: application/json" \
-d '{"username": "user", "password": "pass"}'
```

### Adicionar Produto
```bash
curl -X POST http://127.0.0.1:5000/api/products/add \
-H "Content-Type: application/json" \
-d '{"name": "Produto 1", "price": 29.99, "description": "Descrição"}'
```

## Licença

Este projeto está licenciado sob a [MIT License](LICENSE).

## Contato

Para dúvidas ou sugestões, entre em contato através do [gugasilva.machado@gmail.com](mailto:gugasilva.machado@gmail.com).