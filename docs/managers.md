# Managers

## Introdução

Os *managers* no AgtecCore servem para automatizar a geração de código no projeto, facilitando tarefas repetitivas e mantendo o padrão DRY (*Don’t Repeat Yourself*).

---

## Seções de Manager

### Manager Build

É o comando principal para gerar artefatos de uma aplicação (app).

#### Parâmetros

- `app` (Obrigatório) – Nome da aplicação  
- `model` (Opcional) – Nome do model  
- `templates` (Opcional) – Templates customizados  
- `fields_display` (Opcional) – Campos a serem exibidos  
- `fk_fields_modal` (Opcional) – Chaves estrangeiras exibidas em modal  
- `url` (Opcional)  
- `forms` (Opcional)  
- `views` (Opcional)  
- `renderhtml` (Opcional)  
- `format` (Opcional)  
- `api` (Opcional)

#### Exemplo de uso

```bash
python manage.py build nome_da_app
