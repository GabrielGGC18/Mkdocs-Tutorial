# Django REST Framework

## Introdução

Framework utilizado para criar APIs seguindo o padrão REST.

---

## Instalação

Adicione o pacote ao seu projeto:

```python
INSTALLED_APPS = [
    ...
    'rest_framework',
]
```

---

## Configuração do REST_FRAMEWORK

### Paginação

```python
REST_FRAMEWORK = {
    'DEFAULT_PAGINATION_CLASS': 'rest_framework.pagination.PageNumberPagination',
    'PAGE_SIZE': 10,  # Altere conforme necessário
}
```

### Filtros

```python
REST_FRAMEWORK = {
    'DEFAULT_FILTER_BACKENDS': [
        'django_filters.rest_framework.DjangoFilterBackend',
    ],
}
```

### Autenticação

```python
REST_FRAMEWORK = {
    'DEFAULT_AUTHENTICATION_CLASSES': [
        'rest_framework.authentication.BasicAuthentication',
        'rest_framework.authentication.SessionAuthentication',
        'rest_framework_simplejwt.authentication.JWTAuthentication',
    ],
}
```

### Renderers e Parsers

```python
REST_FRAMEWORK = {
    'DEFAULT_RENDERER_CLASSES': (
        'rest_framework_rapidjson.renderers.RapidJSONRenderer',
    ),
    'DEFAULT_PARSER_CLASSES': (
        'rest_framework_rapidjson.parsers.RapidJSONParser',
    ),
}
```

### Exemplo Completo

```python
REST_FRAMEWORK = {
    'DEFAULT_FILTER_BACKENDS': [
        'django_filters.rest_framework.DjangoFilterBackend',
    ],
    'DEFAULT_AUTHENTICATION_CLASSES': [
        'rest_framework.authentication.BasicAuthentication',
        'rest_framework.authentication.SessionAuthentication',
        'rest_framework_simplejwt.authentication.JWTAuthentication',
    ],
    'DEFAULT_PAGINATION_CLASS': 'rest_framework.pagination.PageNumberPagination',
    'PAGE_SIZE': 50,
}
```

---

## Serializers

### Exemplo de Serializer

```python
class UsuarioSerializer(ModelSerializer):
    """Serializer para o model Usuario (POST, PUT, PATCH, DELETE)"""
    class Meta:
        model = Usuario
        fields = '__all__'
```

### Serializer para GET

```python
class UsuarioGETSerializer(FieldsListSerializerMixin, ModelSerializer):
    """Serializer para o model Usuario (GET)"""
    class Meta:
        model = Usuario
        fields = '__all__'
```

---

## Views

### Permissões

O decorator `@permission_classes([IsAuthenticated, ])` garante que apenas usuários autenticados acessem os endpoints.

### View para métodos de escrita

```python
@permission_classes([IsAuthenticated, ])
class UsuarioViewAPI(ModelViewSet):
    """Gerencia POST, PUT, PATCH, DELETE"""
    queryset = Usuario.objects.select_related().all()
    serializer_class = UsuarioSerializer
```

### View para métodos de leitura

```python
@permission_classes([IsAuthenticated, ])
class UsuarioGETAPI(OptimizedQuerySetMixin, ReadOnlyModelViewSet):
    """Gerencia GET, com filtros e buscas"""
    queryset = Usuario.objects.select_related().all()
    serializer_class = UsuarioGETSerializer
    filter_backend = [filters.SearchFilter]
    filterset_fields = []  # Campos para filtro
    search_fields = []     # Campos para busca
```

---

## URLs

### api_urls.py

```python
from .api_views import UsuarioViewAPI, UsuarioGETAPI
from rest_framework import routers

router = routers.DefaultRouter()
router.register(r'usuario', UsuarioViewAPI, 'usuario-api')
router.register(r'usuario-get', UsuarioGETAPI, 'usuario-get-api')

urlpatterns = router.urls
```

### urls.py da app

Adicione o path abaixo para incluir as rotas da API:

```python
path('api/usuario/', include('usuario.api_urls')),
```

---

## Links Úteis

- [Django REST Framework - Documentação Oficial](https://agtecpalmas.github.io/AgtecCore/django_rest_framework/)
- [Pip](https://pypi.org/project/djangorestframework/)
- [Docs](https://www.django-rest-framework.org/)