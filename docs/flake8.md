# Flake8

## Introdução

O **Flake8** é uma ferramenta que verifica se o código Python está seguindo os padrões de qualidade definidos pelas PEPs (Python Enhancement Proposals), especialmente a PEP 8.

---

## Instalação

Instale o Flake8 via pip:

```bash
pip install flake8
```

---

## Configuração

Na raiz do projeto, crie ou edite o arquivo `.flake8` para configurar o comportamento da ferramenta. Exemplo de configuração padrão:

```ini
[flake8]
max-line-length = 120
exclude = .venv
```

- **max-line-length**: Define o limite de caracteres por linha (padrão: 120).
- **exclude**: Diretórios ou arquivos ignorados pela análise (exemplo: `.venv`).

---

## Execução

Para rodar o Flake8 e analisar o código do projeto, utilize o comando:

```bash
flake8
```

Você pode especificar arquivos ou diretórios:

```bash
flake8 caminho/do/arquivo.py
flake8 caminho/do/diretorio/
```

---

## Exemplo de Saída

Se houver problemas, o Flake8 exibirá mensagens como:

```
caminho/arquivo.py:10:5: E303 too many blank lines (2)
caminho/arquivo.py:15:1: W391 blank line at end of file
```

---

## Links Úteis

- [Flake8 - Documentação Oficial](https://agtecpalmas.github.io/AgtecCore/flake8/)
- [Pip](https://pypi.org/project/flake8/)
- [Docs](https://flake8.pycqa.org/en/latest/)