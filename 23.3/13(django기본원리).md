# django 원리

## 1. 템플릿의 html에서 기능(껍데기) 추가 하고 링크 연결 


```
<a href="{% url 'pybo:question_create' %}" class="btn btn-primary">질문 등록하기</a>
```


## 2. URL 맵핑

* app(프로젝트 하위폴더)에 urls.py 에 url 매핑 규칙 추가

```
urlpatterns = [
    path('question/create/', views.question_create, name='question_create'),
]
```

## 3. form (페이지 요청시 전잘되는 파라미터들을 쉽게 관리하기 위해 사용)
* 폼은 필수 파라미터의 값이 누락되지 않았는지, 파라미터의 형식은 적절한지 등을 검증할 목적으로 사용
*  HTML을 자동으로 생성하거나 폼에 연결된 모델을 이용하여 데이터를 저장하는 기능
```
from django import forms
from pybo.models import Question


class QuestionForm(forms.ModelForm):
    class Meta:
        model = Question  # 사용할 모델
        fields = ['subject', 'content']  # QuestionForm에서 사용할 Question 모델의 속성
```

## 4. app에 views.py에 기능 함수 정의

```
from .forms import QuestionForm # .forms 같은 폴더에 있는 forms 파일에 QuestionForm 함수(모델) import

def question_create(request): # 질문 등록하는 기능 함수 
    form = QuestionForm()
    return render(request, 'pybo/question_form.html', {'form': form})

```


## 5. 템플릿작성 (views에서 정한 경로 파일 생성)

```
{% extends 'base.html' %}
{% block content %}
<div class="container">
    <h5 class="my-3 border-bottom pb-2">질문등록</h5>
    <form method="post">
        {% csrf_token %}
        {{ form.as_p }}
        <button type="submit" class="btn btn-primary">저장하기</button>
    </form>
</div>
{% endblock %}

```


* 한줄요약 app urls.py에서 사용할 path 정의 ->  app views.py에서 기능 함수 정의 -> 기능함수에 정의된 템플릿 작성 
