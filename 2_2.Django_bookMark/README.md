# 세 번째 예제 설명
- 게시판을 통한 CRUD 작성

## List와 작성 페이지 구현

### bookmark/view.py에 BookmarkCreateView 추가

```python
from django.shortcuts import render
from django.views.generic.list import ListView
from django.views.generic.edit import CreateView,UpdateView, DeleteView
from django.views.generic.detail import DetailView
from django.urls import reverse_lazy
# Create your views here.

from .models import Bookmark

class BookmarkListView(ListView):
    model = Bookmark

##Create Bookmark 메서드 추가
class BookmarkCreateView(CreateView):
    model = Bookmark
    fields = ['site_name','url']
    success_url = reverse_lazy('list')
    template_name_suffix = '_create'
```

### 뷰 연결, bookmark/urls.py

```python
from django.urls import path
from .views import BookmarkListView, BookmarkCreateView, BookmarkDetailView, BookmarkUpdateView, BookmarkDeleteView

urlpatterns = [
    path('', BookmarkListView.as_view(), name='list'),
    path('add/', BookmarkCreateView.as_view(), name='add')
]
```

### 템플릿 등록, bookmark/templates/bookmark/bookmark_create.html

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>woolbro bookmark</title>
</head>
<body>
    <form action = "" method = "post">
        {% csrf_token %}
        {{form.as_p}}
        <input type = "submit" value="Add" class = "btn btn-info btn-sm">
    </form>
</body>
</html>
```

### 상세 페이지 

- bookmark/views.py에 상세 정보 추가
```python
##View Detail Bookmark 메서드 추가
class BookmarkDetailView(DetailView):
    model = Bookmark

```

- bookmark/urls.py에 path 추가
```python
from django.urls import path
from .views import BookmarkListView, BookmarkCreateView, BookmarkDetailView

urlpatterns = [
    path('', BookmarkListView.as_view(), name='list'),
    path('add/', BookmarkCreateView.as_view(), name='add'),
    path('detail/<int:pk>/', BookmarkDetailView.as_view(), name='detail')
]
```

- bookmark_detail.html

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>woolbro bookmark</title>
</head>
<body>
    {{object.site_name}}<br/>
    {{object.url}}
</body>
</html>
```

### 북마크 수정 기능 구현

- bookmark/view.html 수정

```python
from django.shortcuts import render
from django.views.generic.list import ListView
from django.views.generic.edit import CreateView,UpdateView
from django.views.generic.detail import DetailView
from django.urls import reverse_lazy
# Create your views here.

from .models import Bookmark

class BookmarkListView(ListView):
    model = Bookmark

##Create Bookmark 메서드 추가
class BookmarkCreateView(CreateView):
    model = Bookmark
    fields = ['site_name','url']
    success_url = reverse_lazy('list')
    template_name_suffix = '_create'

##View Detail Bookmark 메서드 추가
class BookmarkDetailView(DetailView):
    model = Bookmark


##Update View Bookmark 메서드 추가
class BookmarkUpdateView(UpdateView):
    model = Bookmark
    fields = ['site_name','url']
    template_name_suffix = '_update'
```

- bookmark/urls.py 수정

```pthon
from django.urls import path
from .views import BookmarkListView, BookmarkCreateView, BookmarkDetailView, BookmarkUpdateView

urlpatterns = [
    path('', BookmarkListView.as_view(), name='list'),
    path('add/', BookmarkCreateView.as_view(), name='add'),
    path('detail/<int:pk>/', BookmarkDetailView.as_view(), name='detail'),
    path('update/<int:pk>/', BookmarkUpdateView.as_view(), name='update'),
]
```

- bookmark_update.html
```python
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>woolbro bookmark</title>
</head>
<body>
    <form action = "" method = "post">
        {% csrf_token %}
        {{form.as_p}}
        <input type = "submit" value="Update" class = "btn btn-info btn-sm">
    </form>
</body>
</html>
```

### 북마크 삭제 기능 구현

- bookmark/views.py 수정

```python
from django.shortcuts import render
from django.views.generic.list import ListView
from django.views.generic.edit import CreateView,UpdateView, DeleteView
from django.views.generic.detail import DetailView
from django.urls import reverse_lazy
# Create your views here.

from .models import Bookmark

class BookmarkListView(ListView):
    model = Bookmark

##Create Bookmark 메서드 추가
class BookmarkCreateView(CreateView):
    model = Bookmark
    fields = ['site_name','url']
    success_url = reverse_lazy('list')
    template_name_suffix = '_create'

##View Detail Bookmark 메서드 추가
class BookmarkDetailView(DetailView):
    model = Bookmark


##Update View Bookmark 메서드 추가
class BookmarkUpdateView(UpdateView):
    model = Bookmark
    fields = ['site_name','url']
    template_name_suffix = '_update'

class BookmarkDeleteView(DeleteView):
    model = Bookmark
    success_url = reverse_lazy('list')
```

- bookmark/urls 수정

```python
from django.urls import path
from .views import BookmarkListView, BookmarkCreateView, BookmarkDetailView, BookmarkUpdateView, BookmarkDeleteView

urlpatterns = [
    path('', BookmarkListView.as_view(), name='list'),
    path('add/', BookmarkCreateView.as_view(), name='add'),
    path('detail/<int:pk>/', BookmarkDetailView.as_view(), name='detail'),
    path('update/<int:pk>/', BookmarkUpdateView.as_view(), name='update'),
    path('delete/<int:pk>/', BookmarkDeleteView.as_view(), name='delete'),
]

```

- bookmark_confirm_delete.html 생성
```python
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>woolbro bookmark</title>
</head>
<body>
    <form action = "" method = "post">
        {% csrf_token %}
        <div class="alert alert-danger">Do you want to delete "{{object}}" ???? Are you Sure?</div>
        <input type = "submit" value="Delete" class = "btn btn-info btn-sm">
    </form>
</body>
</html>
```




     
    
    
