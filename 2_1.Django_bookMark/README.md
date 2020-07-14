# 두 번째 예제 설명
- 템플릿 확장

## 프로젝트 루트 폴더 밑에 template/base.html 생성

## config/settings.py 수정

- TEMPLATES 옵션의 'DIRS'에 os.path.join(BASE_DIR,"templates") 추가

```python
TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [os.path.join(BASE_DIR,"templates")],
        'APP_DIRS': True,
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
            ],
        },
    },
]
```

## templates/base.html 수정

```python
<!DOCTYPE html> 
<html lang="en"> 
    <head> 
        <meta charset="UTF-8"> 
        <title>
            {% block title %} 
            {% endblock %}
        </title> 
    </head> 

    <body> 
        {% block content %} 
        {% endblock %} 
    </body> 
</html>

```

## bookmark/templates/bookmark/bookmark_confirm_delete.html

```python
{% extends 'base.html' %} 
{% block title %}
    Confirm Delete{% endblock %} 
{% block content %} 

<form action="" method="post"> 
    {% csrf_token %} 
    <div class="alert alert-danger">Do you want to delete Bookmark "{{object}}"??</div> 
    <input type="submit" value="Delete" class="btn btn-danger"> 
</form> 

{% endblock %}

```

## bookmark/templates/bookmark/bookmark_create.html

```python
{% extends 'base.html' %} 
{% block title %}woolbro bookmark{% endblock %} 
{% block content %} 

    <form action = "" method = "post"> 
        {% csrf_token %} {{form.as_p}} 
        <input type = "submit" value="Add" class = "btn btn-info btn-sm"> 
    </form> 
    
{% endblock %}

```

## bookmark/templates/bookmark/bookmark_detail.html

```python
{% extends 'base.html' %} 
{% block title %}woolbro bookmark{% endblock %} 
{% block content %} 
    {{object.site_name}}<br/> 
    {{object.url}} 
    
{% endblock %}

```

## bookmark/templates/bookmark/bookmark_list.html

```python
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>woolbro bookmark</title>
</head>
<body>
    <div class="btn-group">
        <a href ="#" class = "btn btn-info">Add Bookmark</a>
    </div>
    <p></p>
    <table class = "table">
        <thead>
            <tr>
                <th scope = "col">#</th>
                <th scope = "col">Site</th>
                <th scope = "col">URL</th>
                <th scope = "col">Modify</th>
                <th scope = "col">Delete</th>
            </tr>
        </thead>
        <tbody>
            {% for bookmark in object_list %}
            <tr>
                <td>{{forloop.counter}}</td>
                <td><a href="#">{{bookmark.site_name}}</a></td>
                <td><a href="{{bookmark.url}}" target="_blank">{{bookmark.url}}</a> </td>
                <td><a href="#" class="btn btn-success btn-sm">Modify</a></td>
                <td><a href="#" class="btn btn-danger btn-sm">Delete</a></td>
            </tr>
            {% endfor %}
        </tbody>
    </table>
</body>
</html>
```

## bookmark/templates/bookmark/bookmark_update.html

```python
{% extends 'base.html' %} 
{% block title %}woolbro bookmark{% endblock %} 
{% block content %} 
    <form action = "" method = "post"> 
        {% csrf_token %} {{form.as_p}} 
        <input type = "submit" value="Update" class = "btn btn-info btn-sm"> 
    </form> 
{% endblock %}

```
    
