---
title: "Wyświetlanie tekstu na stronie sieci Web (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- JavaScript, write
- JavaScript, writing text
ms.assetid: 3c2455e7-2402-45f2-9545-77a2b2490527
caps.latest.revision: "30"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a8c9ea9d0e0300a0d9b71b0b33d7c99c9ac3935c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="displaying-text-in-a-webpage-javascript"></a>Wyświetlanie tekstu na stronie sieci Web (JavaScript)
Istnieje wiele sposobów, aby wyświetlić tekst na stronie sieci Web. Każda ma zalety i wady i obsługuje określonych celów.  
  
## <a name="displaying-text"></a>Wyświetlanie tekstu  
  
-   Zalecanym sposobem wyświetlania tekstu jest Utwórz element i zapisywania jej właściwość textContent.  
  
    ```JavaScript  
    <div id="textDiv"></div>  
    <script type="text/javascript">  
        var div = document.getElementById("textDiv");  
        div.textContent = "my text";  
        var text = div.textContent;  
    </script>  
    ```  
  
     W tym przykładzie wartość `text` jest "tekst". Jednakże, wynikające z pobierania lub ustawiania wartości `textContent` właściwość węzła nadrzędnego może obejmować zawartości tekstowej z elementów podrzędnych węzłów. W poniższym przykładzie pokazano, że `textContent` oznacza to zestaw na węzeł podrzędny znajduje się w wartości `textContent` węzła nadrzędnego:  
  
    ```JavaScript  
    <div id="textDiv">  
        <div id="nested"></div>  
    </div>  
    <script type="text/javascript">  
        var div = document.getElementById("textDiv");  
        var nestedDiv = document.getElementById("nested");  
        nestedDiv.textContent = "nested";  
  
        var text = "[" + div.textContent + "]";  
    </script>  
    ```  
  
     W tym przykładzie wartość `text` jest "[nested]".  
  
-   Można utworzyć elementu i zapisać jego [innerHTML](http://msdn.microsoft.com/library/ie/ms533897\(v=vs.85\).aspx) lub [innerText](http://msdn.microsoft.com/library/ie/ms533899\(v=vs.85\).aspx) właściwości. Ustawienie tych właściwości dotyczy jedynie tekstu w elemencie, nie znajduje się w jego elementów podrzędnych. Te właściwości są także niektóre wady:  
  
    -   [InnerText](http://msdn.microsoft.com/library/ie/ms533899\(v=vs.85\).aspx) właściwości nie działa we wszystkich przeglądarkach, więc można go uniknąć ze względu na zgodność.  
  
    -   [InnerText](http://msdn.microsoft.com/library/ie/ms533899\(v=vs.85\).aspx) właściwość dotyczy style CSS i nie pojawia się, jeśli element jest ukryty.  
  
    -   [InnerHTML](http://msdn.microsoft.com/library/ie/ms533897\(v=vs.85\).aspx) właściwości pobiera i ustawia zarówno zagnieżdżonych węzłów i tekst. Jeśli go nie jest zabezpieczony, może zostać wykorzystana do ataków uruchomienie skryptu. Ponadto ustawieniem dla niego tekstu bez tagów HTML spowoduje usunięcie wszystkich uprzednio zestaw węzłów.  
  
-   Można użyć `document.write` metody bez konieczności tworzenia elementu. Jednak za pomocą tej metody powoduje całą stronę sieci web do wyczyszczenia, która nie może być co chcesz.  
  
     W poniższym przykładzie przedstawiono jeden wady używania `document.write`. Skrypt jest przeznaczony do wyświetlania czasu co 5 sekund, ale pokazuje czas tylko dwa razy. W czasie `document.write` jest wywoływana po raz drugi, zakończeniu ładowania, strony i `document.write` następnie czyści całą stronę (wywołuje `document.open`). W tym momencie `ShowTime` funkcja już nie istnieje.  
  
    ```html  
    <!DOCTYPE html>  
    <html>  
    <head>  
    <script type="text/javascript">  
        function ShowTime()  
        {  
            var dt = new Date();  
            document.write(dt.toTimeString());  
            // var elem = document.getElementById("divElem");  
            // elem.textContent = dt.toTimeString();  
            window.setTimeout("ShowTime();", 5000);  
        }  
    </script>  
    </head>  
  
    <body>  
    <script type="text/javascript">  
        ShowTime();  
    </script>  
    <div id="myDiv"></div>  
    </body>  
    </html>  
  
    ```  
  
     Aby rozwiązać poprzedni kod, Usuń wiersz kodu, który zawiera `document.write` i Usuń komentarz komentarzem dwa wiersze kodu, które należy wykonać.  
  
-   Można również użyć `alert``prompt`, lub `confirm` funkcji, która wyświetla komunikat w oknie podręcznym. W większości przypadków nie jest dobrym pomysłem jest wyskakujące okno w przeglądarce sieci web. Większość nowoczesnych przeglądarek mają ustawienia, które automatycznie blokowanie wyskakujących okienek, wiadomości nie może być widoczny. Ponadto istnieje możliwość wprowadzenia nieskończoną pętlę, korzystając z okien wyskakujących uniemożliwiającej użytkownika zamknąć stronę sieci web w zwykły sposób.