---
title: Przybornik, karta HTML
ms.date: 06/21/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.toolbox.html
helpviewer_keywords:
- Toolbox, HTML tab
- HTML Designer, setting options
- HTML tab in Toolbox
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c2d4b3f802b3854fc311a359149f44d75562691e
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34752699"
---
# <a name="toolbox-html-tab"></a>Przybornik, karta HTML

**HTML** karta w przyborniku zawiera składniki, które są przydatne w formularzach sieci Web i stron sieci Web. Aby wyświetlić na tej karcie, należy najpierw otworzyć dokument do edycji w Projektancie HTML. Na **widoku** menu, kliknij przycisk **przybornika**, a następnie kliknij przycisk **HTML** karcie przybornika.

 Można utworzyć wystąpienia narzędzia na **HTML** kartę, albo kliknij dwukrotnie pozycję Narzędzia, aby dodać go do dokumentu do bieżącego punkt wstawiania, lub wybierz narzędzie i przeciągnij go do żądanej pozycji na powierzchni do edycji.

## <a name="ui-elements"></a>Elementy interfejsu użytkownika

Następujące narzędzia są dostępne jako domyślne na karcie HTML.

**Pointer**

![Wskaźnik strony projektanta HTML ASP.NET Mobile](../../ide/reference/media/vxpointer.gif)

To narzędzie jest domyślnie zaznaczona, po otwarciu dowolnej karcie przybornika. Nie można usunąć. Wskaźnik umożliwia przeciągnij obiekty na powierzchnię projektu widoku, zmieniać ich rozmiar i zmiany ich położenia na stronie lub formularza. Aby uzyskać więcej informacji, zobacz [przybornika](../../ide/reference/toolbox.md).

**Dane wejściowe (przycisk)**

![Przycisk HTML strony sieci web](../../ide/reference/media/vxbutton.gif)

Wstawia `input` elementu `type="button"`. Aby zmienić tekst, który jest wyświetlany `name` właściwości. Domyślnie `id="Button1"` jest wstawiany dla przycisku pierwszej `id="Button2"` na sekundę i tak dalej.

Przeciągnięcie **danych wejściowych (przycisk)** na powierzchnię projektu widoku, do dokumentu jest wstawiany kod znaczników HTML podobne do poniższych:

```html
<input id="Button1" type="button" value="Button" name="Button1">
```

**Dane wejściowe (Resetowanie)**

![HTMLpageResetButton — zrzut ekranu](../../ide/reference/media/vxreset.gif)

Wstawia `input` elementu `type="reset"`. Aby zmienić tekst, który jest wyświetlany `name` właściwości. Domyślnie `id="Reset1"` dodaje się pierwszy resetowania przycisku `id="Reset2"` na sekundę i tak dalej.

Przeciągnięcie **dane wejściowe (Resetowanie)** na powierzchnię projektu widoku, do dokumentu jest wstawiany kod znaczników HTML podobne do poniższych:

```html
<input id="Reset1" type="reset" value="Reset" name="Reset1">
```

**Dane wejściowe (Prześlij)**

![HTMLpageToolbarSubmitButton — zrzut ekranu](../../ide/reference/media/vxsubmit.gif)

Wstawia `input` elementu `type="submit"`. Aby zmienić tekst, który jest wyświetlany `name` właściwości. Domyślnie `id="Submit1"` dodaje się do pierwszego przycisku Prześlij `id="Submit2"` na sekundę i tak dalej.

Przeciągnięcie **danych wejściowych (Prześlij)** na powierzchnię projektu widoku, do dokumentu jest wstawiany kod znaczników HTML podobne do poniższych:

```html
<input id="Submit1" type="submit" value="Submit" name="Submit1">
```

**Dane wejściowe (tekst)**

![HTMLpageToolbarTextField — zrzut ekranu](../../ide/reference/media/vxtextfield.gif)

Wstawia `input` elementu `type="text"` w dokumencie. Aby zmienić domyślny tekst, który jest wyświetlany `value` atrybutu. Domyślnie `id="Text1"` jest wstawiana pierwsze pole tekstowe, `id="Text2"` na sekundę i tak dalej.

Przeciągnięcie **danych wejściowych (tekst)** na powierzchnię projektu widoku, do dokumentu jest wstawiany kod znaczników HTML podobne do poniższych:

```html
<input id="Text1" TYPE="text" value="Text Field" name="Text1">
```

> [!IMPORTANT]
>Zaleca się sprawdzenie poprawności wszystkich danych wejściowych użytkownika. Aby uzyskać więcej informacji, zobacz [sprawdzanie poprawności danych wejściowych użytkownika w witrynach składnika ASP.NET Web Pages (Razor)](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites).

**Dane wejściowe (plik)**

![Strona HTML pole pliku](../../ide/reference/media/vxfilefield.gif)

Wstawia `input` elementu `type="file"` w dokumencie. Domyślnie `id="File1"` jest wstawiany pierwszego pola, pliku, `id="File2"` na sekundę i tak dalej.

Przeciągnięcie **danych wejściowych (plik)** na powierzchnię projektu widoku, do dokumentu jest wstawiany kod znaczników HTML podobne do poniższych:

```html
<input id="File1" type="file" name="File1">
```

> [!IMPORTANT]
> Zaleca się sprawdzenie poprawności wszystkich danych wejściowych użytkownika. Aby uzyskać więcej informacji, zobacz [sprawdzanie poprawności danych wejściowych użytkownika w witrynach składnika ASP.NET Web Pages (Razor)](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites).

**Dane wejściowe (hasło)**

![Pole hasła programu Visual Studio](../../ide/reference/media/vxpassword.gif)

Wstawia `input` elementu `type="password"`. Domyślnie `id="Password1"` pierwsze pole hasło jest wstawiana `id="Password2"` na sekundę i tak dalej.

Przeciągnięcie **danych wejściowych (hasło)** na powierzchnię projektu widoku, do dokumentu jest wstawiany kod znaczników HTML podobne do poniższych:

```html
<input id="Password1" type="password" name="Password1">
```

> [!IMPORTANT]
> Jeśli aplikacja przesyła nazwy użytkownika i hasła, należy skonfigurować witryny sieci Web do używania protokołu Secure Sockets Layer (SSL) do szyfrowania transmisji. Aby uzyskać więcej informacji, zobacz "Zabezpieczanie połączeń z protokołu SSL" w [przewodniku obsługi usług IIS](http://go.microsoft.com/fwlink/?linkid=47856). Ponadto zaleca się sprawdzenie poprawności wszystkich danych wejściowych użytkownika. Aby uzyskać więcej informacji, zobacz [sprawdzanie poprawności danych wejściowych użytkownika w witrynach składnika ASP.NET Web Pages (Razor)](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites).

**Dane wejściowe (pole wyboru)**

![HTML strony sieci Web opcja Checkbox w przyborniku](../../ide/reference/media/vxcheckbox.gif)

Wstawia `input` elementu `type="checkbox"`. Aby zmienić tekst, który jest wyświetlany `name` właściwości. Domyślnie `id="Checkbox1"` jest wstawiany pierwszego pola wyboru `id="Checkbox2"` na sekundę i tak dalej.

Przeciągnięcie **danych wejściowych (pole wyboru)** na powierzchnię projektu widoku, do dokumentu jest wstawiany kod znaczników HTML podobne do poniższych:

```html
<input id="Checkbox1" type="checkbox" name="Checkbox1">
```

**Dane wejściowe (przycisk radiowy)**

![VisualStudioHTMLpageRadioButton — zrzut ekranu](../../ide/reference/media/vxradio.gif)

Wstawia `input` elementu `type="radio"`. Aby zmienić tekst, który jest wyświetlany `name` właściwości. Domyślnie `id="Radio1"` dodaje się do pierwszego przycisku radiowego `id="Radio2"` na sekundę i tak dalej.

Przeciągnięcie **danych wejściowych (przycisk radiowy)** na powierzchnię projektu widoku, do dokumentu jest wstawiany kod znaczników HTML podobne do poniższych:

```html
<input id="Radio1" type="radio" name="Radio1">
```

**Dane wejściowe (ukryte)**

![Ukryty element strony HTML](../../ide/reference/media/vxhidden.gif)

Wstawia `input` elementu `type="hidden"`. Domyślnie `id="Hidden1"` dodaje się do pierwszego pola ukrytego `id="Hidden2"` na sekundę i tak dalej.

Przeciągnięcie **danych wejściowych (ukryte)** na powierzchnię projektu widoku, do dokumentu jest wstawiany kod znaczników HTML podobne do poniższych:

```html
<input id="Hidden1" type="hidden" name="Hidden1">
```

**Textarea**

![Pasek narzędzi strony HTML obszaru tekstu](../../ide/reference/media/vxtextarea.gif)

Wstawia `textarea` elementu. Zmień rozmiar obszaru tekstu lub użyj jej paski przewijania, aby wyświetlić tekstu, który wychodzi poza jego obszar wyświetlania. Aby zmienić domyślny tekst, który jest wyświetlany `value` atrybutu. Domyślnie `id="textarea1"` jest wstawiane pierwszego obszaru tekstu `id=" textarea 2"` na sekundę i tak dalej.

Przeciągnięcie **Textarea** na powierzchnię projektu widoku, do dokumentu jest wstawiany kod znaczników HTML podobne do poniższych:

```html
<textarea id=" textarea 1 name=" textarea 1" rows=2 cols=20></textarea>
```

> [!IMPORTANT]
> Zaleca się sprawdzenie poprawności wszystkich danych wejściowych użytkownika. Aby uzyskać więcej informacji, zobacz [sprawdzanie poprawności danych wejściowych użytkownika w witrynach składnika ASP.NET Web Pages (Razor)](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites).

**Tabela**

![HTMLpageToolbarTable — zrzut ekranu](../../ide/reference/media/vxtable.gif)

Wstawia `table` elementu.

Przeciągnięcie **tabeli** na powierzchnię projektu widoku, do dokumentu jest wstawiany kod znaczników HTML podobne do poniższych:

```html
<table cellspacing="1" width="75%" border=1> <tr><td></td></tr></table>
```

**Obraz**

![Strona HTML — element obrazu](../../ide/reference/media/vximage.gif)

Wstawia `img` elementu. Edytuj ten element, aby określić jego `src` i jego `alt` tekstu.

Przeciągnięcie **obrazu** na powierzchnię projektu widoku, do dokumentu jest wstawiany kod znaczników HTML podobne do poniższych:

```html
<img alt="" src="">
```

**Select**

![Strona HTML listy rozwijanej przybornika](../../ide/reference/media/vxdropdown.gif)

Wstawia listy rozwijanej `select` elementu (bez `size` atrybutu). Domyślnie `id="select1"` jest wstawiany pierwszego pola listy, `id="select2"` na sekundę i tak dalej.

Przeciągnięcie **wybierz** na powierzchnię projektu widoku, do dokumentu jest wstawiany kod znaczników HTML podobne do poniższych:

```html
<select id="select1" name="select1"><option selected></option></select>
```

Można utworzyć wiele wierszy `select` elementu przez zwiększenie wartości właściwości size.

**Linia pozioma**

![Strona HTML poziome elementu reguły](../../ide/reference/media/vxhorizontal.gif)

Wstawia `hr` elementu. Aby zwiększyć grubość linii, należy edytować `size` atrybutu.

Przeciągnięcie **poziomą** na powierzchnię projektu widoku, do dokumentu jest wstawiany kod znaczników HTML podobne do poniższych:

```html
<hr width="100%" size=1>
```

**Div**

![Strona HTML etykiety](../../ide/reference/media/vxlabel.gif)

Wstawia `div` element, który zawiera `ms_positioning="FlowLayout"` atrybutu. Z wyjątkiem szerokość i wysokość ten element jest taki sam jak panelu układu przepływu. Formatowanie tekstu, który znajduje się w `div` elementu, Dodaj `class="stylename"` atrybut do tagu otwierającym.

Przeciągnięcie **Div** na powierzchnię projektu widoku, do dokumentu jest wstawiany kod znaczników HTML podobne do poniższych:

```html
<div ms_positioning="FlowLayout" style="width: 70px; position: relative; height: 15px">Label</div>
```

## <a name="see-also"></a>Zobacz także

- [Przybornik](../../ide/reference/toolbox.md)
