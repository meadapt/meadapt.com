---
date: 2025-09-21
draft: false
authors: [gabrielbdornas]
comments: true
categories:
  - Django
  - Rest API
---

# Criando sua primeira API com Django Rest Framework e Poetry

Se você já pensou em criar uma **API** para expor dados de forma organizada e escalável, mas ainda tem dúvidas,
neste post vou te mostrar como.
Vamos criar, do zero, uma API simples para organizar livros.

Para isso vamos utlizar o **Django Rest Framework (DRF)**.
Ele é um dos frameworks mais usados em Python para desenvolvimento de APIs robustas.

Vamos nessa?

<!-- more -->

## Preparando o ambiente com Poetry

Antes de sair instalando bibliotecas aleatoriamente no seu computador, é importante manter o ambiente limpo e organizado.
Para isso, vamos usar o **Poetry**, uma ferramenta moderna de gerenciamento de dependências em Python.

Começamos criando uma pasta para o projeto:

```bash
mkdir bookstore
cd bookstore
```

Agora inicializamos o Poetry (com a flag `-q` para aceitar as opções padrão sem interagir):

```bash
poetry init -q
```

Instalamos as bibliotecas necessárias:

```bash
poetry add djangorestframework
```

E ativamos o ambiente virtual criado pelo Poetry:

```bash
eval $(poetry env activate)
```

## Criando o projeto Django

Com o ambiente pronto, criamos a estrutura inicial:

```bash
django-admin startproject bookstore .
django-admin startapp book
```

Agora editamos `bookstore/settings.py` e adicionamos o Django Rest Framework e nosso novo app `book`:

```python
INSTALLED_APPS = [
    ...,
    'rest_framework',
    'book',
]
```

## Definindo as rotas

Para organizar melhor nossas rotas, vamos criar um arquivo `book/urls.py` com as rotas do app:

```python
from django.urls import path
from .api import BookListApi, BookCreateApi

urlpatterns = [
    path('list', BookListApi),
    path('create', BookCreateApi),
]
```

E no arquivo principal `bookstore/urls.py` incluímos as rotas do app:

```python
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('book/', include('book.urls')),
]
```

## Criando o modelo de livro

Em `book/models.py`:

```python
from django.db import models

class BookModel(models.Model):
    name = models.CharField(max_length=100)
    author = models.CharField(max_length=100)

    def __str__(self):
        return self.name
```

## Criando os primeiros endpoints da APIs

Agora vem a parte divertida! 😃

Para organizar melhor nossos endpoints, vamos criar um arquivo `book/api.py`.
E nele criamos duas opções, uma para **listar livros** e outra para **criar um novo livro**:

```python
from rest_framework.decorators import api_view
from rest_framework.response import Response
from .models import BookModel

@api_view(['GET'])
def BookListApi(request):
    books = BookModel.objects.all()
    data = [{'name': b.name, 'author': b.author} for b in books]
    return Response(data)

@api_view(['POST'])
def BookCreateApi(request):
    book = BookModel.objects.create(
        name=request.data['name'],
        author=request.data['author']
    )
    return Response({
        'id': book.id,
        'name': book.name,
        'author': book.author
    })
```

## Testando a API

Rodamos as migrações para criar a tabela no banco:

```bash
python manage.py makemigrations
python manage.py migrate
```

Rodamos o servidor:

```bash
python manage.py runserver
```

Agora podemos acessar as rotas:

* `GET /book/list` → retorna todos os livros
* `POST /book/create` → cria um novo livro passando `name` e `author` no corpo da requisição

Você pode testar no **Postman**, no terminal interativo Python usando a biblioteca `requests` ou até mesmo direto pelo `python manage.py shell`.

Obs.: **Não se esqueça de commitar tudo que foi feito até o momento.**

## Conclusão

Com poucos passos criamos uma API funcional utilizando Django Rest Framework. 🎉
Esse é só o começo: com DRF é possível trabalhar com **serializers**, **views genéricas**, **autenticação** e muito mais.

👉 No próximo artigo, vamos aprender a atualizar e excluir registros usando os métodos **PUT** e **DELETE**.
