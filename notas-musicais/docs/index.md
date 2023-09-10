# Configuração do Ambiente de Desenvolvimento

É sempre uma boa estratégia começar pela configuração da documentação.

Mas antes de iniciar a configuração, devemos usar o comando `poetry shell` para acessar o ambiente virtual criado pelo [poetry]


## Configurando a Ferramenta de Documentação `mkdocs`

Para iniciar a configuração da documentação, iniciamos a ferramenta [mkdocs] com o comando `mkdocs new`

~~~
# Criar a Documentação no próprio diretório do pacote
mkdocs new .
~~~

![executando o comando mkdocs new](assets/mkdocs-new.png){ width='500' .center }

A estrtura do Pacote ficou:

~~~
.
├── README.md
├── docs
│   └── index.md
├── mkdocs.yml
├── notas_musicais
│   └── __init__.py
├── poetry.lock
├── pyproject.toml
└── tests
    └── __init__.py

3 directories, 7 files
~~~

Utilizamos o comando `mkdocs serve` para gerar um URL para abrir no Browser a Documentação.

~~~
# Executa o servidor do mkdocs
mkdocs serve
~~~

![executando o comando mkdocs serve](assets/mkdocs-serve.png){ width='500' .center }

Para aplicar o tema [mkdocs-material] e utilizar o idioma português, precisamos editar o arquivo `mkdocs.yml`:

~~~
site_name: Notas Musicais

theme:
  name: material
  language: pt-BR

~~~

- o **yaml** utiliza 2 espaçamentos na sintaxe.

- os temas disponíveis são: **material**, **mkdocs** e **readthedocs**

Agora para tornar o Repositório no Github acessível atarvés da documentação, faça a seguinte edição no `mkdocs.yaml`:

~~~
site_name: Notas Musicais
repo_url: https://github.com/rib-thiago/notas-musicais
repo_name: rib-thiago/notas-musicais
edit_uri: /tree/main/docs

theme:
  name: material
  language: pt-BR

~~~

- repo_url indica o reposirório da aplicação
- repo_name indica o nome de exibição do repositório na aplicação
- edit_uri indica o path exato para editar a documentação


Para alterar favicon e logo, primeiro é preciso criar um diretório para os arquivos estáticos dentro de `docs/`, chamado `docs/assets/` e inserir dentro dele o arquivo utilizado para logo e favicon. Após isso, editar novamente o `mkdocs.yaml`:

~~~
site_name: Notas Musicais
repo_url: https://github.com/rib-thiago/notas-musicais
repo_name: rib-thiago/notas-musicais
edit_uri: /tree/main/docs

theme:
  name: material
  language: pt-BR
  logo: assets/python.png
  favicon: assets/python.png
~~~

**Para alterar o conteúdo da documentação** editamos o arquivo `docs/index.md`

Inserir imagem na documentação com a seguinte sintaxe:

~~~
![<descrição>](caminho/relativo){atributos}
~~~

- Os atributos funcionam graças à extensão [PyMdown Extensions] que vem instalada com o [mkdocs-material], por isso é preciso editar o arquivo `mkdocs.yaml`:

~~~
site_name: Notas Musicais
repo_url: https://github.com/rib-thiago/notas-musicais
repo_name: rib-thiago/notas-musicais
edit_uri: /tree/main/docs

theme:
  name: material
  language: pt-BR
  logo: assets/python.png
  favicon: assets/python.png

markdown_extensions:
  - attr_list
~~~

A extensão `super-fancies` possui o `attr_list`.

Porém, para injetar CSS no `mkdocs` é preciso outra edição no `mkdocs.yaml`:

~~~
site_name: Notas Musicais
repo_url: https://github.com/rib-thiago/notas-musicais
repo_name: rib-thiago/notas-musicais
edit_uri: /tree/main/docs

theme:
  name: material
  language: pt-BR
  logo: assets/python.png
  favicon: assets/python.png

markdown_extensions:
  - attr_list

extra_css:
  - stylesheets/extra.css
~~~

Criar o diretório e arquivo `docs/stylesheets/extra.css`

___


[poetry]:(https://python-poetry.org/docs/)
[gh]:(https://cli.github.com/manual/)
[ignr]:(https://github.com/Antrikshy/ignr.py)
[pytest]:(https://docs.pytest.org/en/7.1.x/contents.html)
[pytest-cov]:(https://pytest-cov.readthedocs.io/en/latest/)
[coverage]:(https://coverage.readthedocs.io/en/7.3.1/)
[PEP-8]:(https://peps.python.org/pep-0008/)
[blue]:(https://blue.readthedocs.io/en/latest/)
[isort]:(https://pycqa.github.io/isort/)
[mkdocs]:(https://www.mkdocs.org/getting-started/)
[mkdocs-material]:(https://squidfunk.github.io/mkdocs-material/)
[mkdocstrings]:(https://mkdocstrings.github.io/)
[mkdocstrings-python]:(https://mkdocstrings.github.io/python/)
[taskipy]:(https://github.com/taskipy/taskipy)
[PyMdown Extensions]:(https://facelessuser.github.io/pymdown-extensions/)