---
title: Samouczek — Dowiedz się Django w programie Visual Studio, krok 5
description: Wskazówki dotyczące podstawy Django w kontekście projektów programu Visual Studio, w szczególności funkcje uwierzytelniania określonych przez Szablony projektów sieci Web Django.
ms.date: 04/25/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: e2c5f9461eafa83551ba15c36d8ef212922a52ff
ms.sourcegitcommit: 56018fb1f52f17bf35ae2ce71c50c763486e6173
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="tutorial-step-5-authenticate-users-in-django"></a>Samouczek krok 5: uwierzytelnianie użytkowników w Django

**Poprzedni krok: [użyj pełnego szablonu projektu sieci Web Django](learn-django-in-visual-studio-step-04-full-django-project-template.md)**

Ponieważ uwierzytelnianie jest potrzeba wspólne dla aplikacji sieci web, szablon "Projektu sieci Web Django" obejmuje przepływ uwierzytelniania podstawowego. (Szablon "Projektu sieci Web Django sond" omówione w kroku 6 ten samouczek zawiera również takim samym przepływie.) W przypadku stosowania Django szablony projektu Visual Studio obejmuje wszystkie moduły niezbędne do uwierzytelniania w projekcie Django `settings.py`.

W tym kroku dowiesz się:

> [!div class="checklist"]
> - Jak używać przebieg uwierzytelniania w szablony programu Visual Studio (krok 5 - 1)

## <a name="step-5-1-use-the-authentication-flow"></a>Krok 5-1: Użyj przepływ uwierzytelniania

Poniższe kroki wykonuje przepływ uwierzytelniania i opisano części projektu, które są związane z:

1. Jeśli nie zostały już wykonane z instrukcjami wyświetlanymi w `readme.html` pliku w katalogu głównym projektu, aby utworzyć konta administratora (administrator), zrób to teraz.

1. Uruchamianie aplikacji z programu Visual Studio za pomocą **debugowania** > **Rozpocznij debugowanie** (F5). Gdy aplikacja zostanie wyświetlona w przeglądarce, która obserwować **Zaloguj** zostanie wyświetlona w prawym górnym rogu paska nawigacyjnego.

    ![Na stronie aplikacji Django Web Project formantu logowania](media/django/step05-login-control.png)

1. Otwórz `templates/app/layout.html` i że `<div class="navbar ...>` element zawiera tag `{% include app/loginpartial.html %}`. `{% include %}` Tag nakazuje systemowi tworzenia szablonów w Django ściągnąć zawartość pliku uwzględnione w tym momencie zawierającego szablonu.

1. Otwórz `templates/app/loginpartial.html` i sprawdź, jak używa tagu warunkowego `{% if user.is_authenticated %}` wraz z programem `{% else %}` tag do renderowania różne elementy interfejsu użytkownika, w zależności od tego, czy użytkownik został uwierzytelniony:

    ```html
    {% if user.is_authenticated %}
    <form id="logoutForm" action="/logout" method="post" class="navbar-right">
        {% csrf_token %}
        <ul class="nav navbar-nav navbar-right">
            <li><span class="navbar-brand">Hello {{ user.username }}!</span></li>
            <li><a href="javascript:document.getElementById('logoutForm').submit()">Log off</a></li>
        </ul>
    </form>

    {% else %}

    <ul class="nav navbar-nav navbar-right">
        <li><a href="{% url 'login' %}">Log in</a></li>
    </ul>

    {% endif %}
    ```

1. Ponieważ żaden użytkownik nie jest uwierzytelniony przy pierwszym uruchomieniu aplikacji, ten kod szablonu renderuje tylko "Zaloguj" łącze do ścieżki względnej "login". Jak określono w `urls.py` opisane w poprzedniej sekcji, że trasy jest mapowany na `django.contrib.auth.views.login` widok, w którym znajduje się następujące dane:

    ```python
    {
        'template_name': 'app/login.html',
        'authentication_form': app.forms.BootstrapAuthenticationForm,
        'extra_context':
        {
            'title': 'Log in',
            'year': datetime.now().year,
        }
    }
    ```

    W tym miejscu `template_name` identyfikuje szablon na stronie logowania, w tym przypadku `templates/app/login.html`. `extra_context` Właściwość została dodana do dane kontekstu domyślnego na szablon. Na koniec `authentication_form` Określa klasę formularza, aby za pomocą nazwy logowania "w szablonie jest widoczny jako `form` obiektu. Wartość domyślna to `AuthenticationForm` (z `django.contrib.auth.views`); szablon projektu Visual Studio używa zamiast tego formularza, określonych w aplikacji `forms.py` pliku:

    ```python
    from django import forms
    from django.contrib.auth.forms import AuthenticationForm
    from django.utils.translation import ugettext_lazy as _

    class BootstrapAuthenticationForm(AuthenticationForm):
        """Authentication form which uses boostrap CSS."""
        username = forms.CharField(max_length=254,
                                   widget=forms.TextInput({
                                       'class': 'form-control',
                                       'placeholder': 'User name'}))
        password = forms.CharField(label=_("Password"),
                                   widget=forms.PasswordInput({
                                       'class': 'form-control',
                                       'placeholder':'Password'}))
    ```

    Jak widać, ta klasa formularza jest pochodną `AuthenticationForm` i zastąpi pola nazwy użytkownika i hasła, aby dodać tekst zastępczy. Szablon programu Visual Studio zawiera ten kod jawne przy założeniu, że prawdopodobnie należy do dostosowywania formularza, takie jak dodawanie walidacji siły hasła.

1. Po przejściu do strony logowania, następnie renderuje aplikacji `login.html` szablonu. Zmienne `{{ form.username }}` i `{{ form.password }}` renderowania `CharField` formularzy z `BootstrapAuthenticationForm`. Istnieje również wbudowane sekcję, aby wyświetlić błędy sprawdzania poprawności, a element gotowych do logowania społecznościowych, jeśli użytkownik chce dodać tych usług.

    ```html
    {% extends "app/layout.html" %}

    {% block content %}

    <h2>{{ title }}</h2>
    <div class="row">
        <div class="col-md-8">
            <section id="loginForm">
                <form action="." method="post" class="form-horizontal">
                    {% csrf_token %}
                    <h4>Use a local account to log in.</h4>
                    <hr />
                    <div class="form-group">
                        <label for="id_username" class="col-md-2 control-label">User name</label>
                        <div class="col-md-10">
                            {{ form.username }}
                        </div>
                    </div>
                    <div class="form-group">
                        <label for="id_password" class="col-md-2 control-label">Password</label>
                        <div class="col-md-10">
                            {{ form.password }}
                        </div>
                    </div>
                    <div class="form-group">
                        <div class="col-md-offset-2 col-md-10">
                            <input type="hidden" name="next" value="/" />
                            <input type="submit" value="Log in" class="btn btn-default" />
                        </div>
                    </div>
                    {% if form.errors %}
                    <p class="validation-summary-errors">Please enter a correct user name and password.</p>
                    {% endif %}
                </form>
            </section>
        </div>
        <div class="col-md-4">
            <section id="socialLoginForm"></section>
        </div>
    </div>

    {% endblock %}
    ```

1. Po przesłaniu formularza Django podejmie próbę uwierzytelniania poświadczenia podane przez użytkownika (na przykład poświadczenia użytkownika nadrzędnego). Jeśli uwierzytelnianie nie powiedzie się, nadal będą na tej samej stronie, ale `form.errors` ustawioną na true. Jeśli uwierzytelnianie zakończy się pomyślnie, Django przechodzi do względny adres URL w polu "dalej" `<input type="hidden" name="next" value="/" />`, czyli w tym przypadku strony głównej (`/`).

1. Teraz, gdy strona główna jest renderowany ponownie, `user.is_authenticated` właściwość ma wartość true, gdy `loginpartial.html` renderowania szablonu. W związku z tym zostanie wyświetlony komunikat "Hello (nazwa_użytkownika)" i "Wyloguj". Można użyć `user.is_authenticated` w innych częściach aplikacji, aby sprawdzić uwierzytelniania.

    ![Witaj wiadomości i wylogowywania kontrolki na stronie aplikacji projektu sieci Web Django](media/django/step05-logoff-control.png)

1. Aby sprawdzić, czy uwierzytelniony użytkownik jest autoryzowany do dostępu do określonych zasobów, należy pobrać uprawnienia specyficzne dla użytkownika z bazy danych dla tego użytkownika. Aby uzyskać więcej informacji, zobacz [przy użyciu uwierzytelniania systemu Django](https://docs.djangoproject.com/en/2.0/topics/auth/default/#permissions-and-authorization) (Django dokumentów).

1. Administratora lub administratora, w szczególności jest autoryzowany do dostępu wbudowanych interfejsy administratora Django, użyj względnych adresów URL "/admin/" i "/ admin/doc /". Aby włączyć te interfejsy, otwórz projekt Django `urls.py` i Usuń komentarze z poniższych:

    ```python
    from django.conf.urls import include
    from django.contrib import admin
    admin.autodiscover()

    # ...
    urlpatterns = [
        # ...
        url(r'^admin/doc/', include('django.contrib.admindocs.urls')),
        url(r'^admin/', include(admin.site.urls)),
    ]
    ```

    Po ponownym uruchomieniu aplikacji, można przejść do "/admin/" i "/ admin/doc /" i wykonywać zadania, takie jak utworzenie dodatkowych kont użytkowników.

    ![Interfejs administratora Django](media/django/step05-administrator-interface.png)

1. Ostatnia sekcja przepływ uwierzytelniania jest wylogowanie. Jak widać w `loginpartial.html`, **wylogować** łącze jest po prostu POST względny adres URL "/ logowania", który jest obsługiwany przez wbudowane widoku `django.contrib.auth.views.logout`. Ten widok nie powoduje wyświetlenia elementów interfejsu użytkownika i tylko przechodzi do strony głównej (jak pokazano w `urls.py` dla "^ wylogowania$" wzorzec). Jeśli chcesz wyświetlić stronę wylogowania, najpierw zmień wzorca adresu URL w następujący sposób, aby dodać właściwość "template_name" i Usuń właściwość "next_page":

    ```python
    url(r'^logout$',
        django.contrib.auth.views.logout,
        {
            'template_name': 'app/loggedoff.html',
            # 'next_page': '/',
        },
        name='logout')
    ```

    Następnie utwórz `templates/app/loggedoff.html` z następującą zawartość (minimalny):

    ```html
    {% extends "app/layout.html" %}
    {% block content %}
    <h3>You have been logged off</h3>
    {% endblock %}
    ```

    Wynik wygląda następująco:

    ![Dodaje wylogowany strony](media/django/step05-logged-off-page.png)

1. Gdy wszystko gotowe, Zatrzymaj serwer i ponownie przekazać zmiany do kontroli źródła.

### <a name="question-what-is-the-purpose-of-the--crsftoken--tag-that-appears-in-the-form-elements"></a>Pytanie: co to jest celem {% crsf_token %} tagów, które pojawia się w \<formularza\> elementy?

Odpowiedź: `{% crsf_token %}` znacznik zawiera wbudowane w Django [międzylokacyjnej ochrony sfałszowaniem (crsf) żądania](https://docs.djangoproject.com/en/2.0/ref/csrf/) (Django dokumentów). Zwykle Dodaj ten tag do elementów, które obejmuje metody żądania POST, PUT i DELETE, takie jak formularz, a funkcja renderowania szablonu (`render`) wstawia potrzeby ochrony.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Należy użyć szablonu projektu sieci Web Django sond](learn-django-in-visual-studio-step-06-polls-django-web-project-template.md)

## <a name="going-deeper"></a>Przechodząc głębiej

- [Uwierzytelnianie użytkownika w Django](https://docs.djangoproject.com/en/2.0/topics/auth/) (docs.djangoproject.com)
- Kod źródłowy samouczek w witrynie GitHub: [Microsoft/python — przykładowy — vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)