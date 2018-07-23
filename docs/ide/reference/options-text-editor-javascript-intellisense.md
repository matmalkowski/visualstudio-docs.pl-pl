---
title: Opcje, edytor tekstu, JavaScript, IntelliSense
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Intellisense.References
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Intellisense.General
ms.assetid: b4a9816d-cf87-4dc6-a8d4-1591d6a48103
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 584f2496e676b37b23afbe9b4e135f475a73d8df
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2018
ms.locfileid: "39179752"
---
# <a name="options-text-editor-javascript-intellisense"></a>Opcje, edytor tekstu, JavaScript, IntelliSense
Użyj **IntelliSense** strony **opcje** okno dialogowe, aby zmodyfikować ustawienia, które wpływają na działanie technologii IntelliSense dla języka JavaScript. Możesz uzyskać dostęp **IntelliSense** strony, wybierając **narzędzia**, **opcje** na pasku menu, a następnie rozwijając **edytora tekstów**,  **JavaScript**, **IntelliSense.**

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

**IntelliSense** strona zawiera następujące sekcje:

## <a name="validation"></a>Walidacja
 Te opcje służą do ustawiania preferencji, w jaki sposób edytor kodu JavaScript sprawdza poprawność składni w dokumencie.

## <a name="uielement-list"></a>Lista elementów UI
 **Pokaż błędy składniowe**

 Gdy to pole wyboru nie jest zaznaczone, edytor kodu JavaScript nie pokazuje błędów składniowych. Jest to przydatne, jeśli pracujesz z nieswoim kodem, w którym nie zamierzasz naprawiać błędów składniowych.

 Gdy to pole wyboru jest zaznaczone, masz możliwość dokonania wyboru **Pokaż błędy jako ostrzeżenia** pole wyboru.

 **Pokaż błędy jako ostrzeżenia**

 Gdy to pole wyboru jest zaznaczone, błędy JavaScript są pokazywane jako ostrzeżenia zamiast błędów na liście błędów.

 **Pobierz zdalne odwołania (np. http://) dla plików w projekcie plików pozostałych**

 Gdy to pole wyboru jest zaznaczone i gdy masz plik JavaScript otwarty poza kontekstem projektu, Visual Studio pobierze zdalne pliki JavaScript, do których odwołuje się plik w celu dostarczania informacji w technologii IntelliSense. Gdy ta opcja jest zaznaczona, pliki zostaną pobrane po włączeniu ich jako odwołania w pliku JavaScript.

> [!NOTE]
> Dla projektów sieci web domyślnie pobierane są pliki zdalne, do którego odwołuje się projekt.


## <a name="statement-completion"></a>Dokańczanie instrukcji
 Możesz użyć tych opcji do zmiany zachowania dokańczania instrukcji IntelliSense.

## <a name="uielement-list"></a>Lista elementów UI
 **Używaj tylko tabulatora lub enter, aby zatwierdzić**

 Gdy to pole wyboru jest zaznaczone, edytor kodu JavaScript dołącza instrukcje z elementami zaznaczonymi na liście dokańczania dopiero po wybraniu klawisza Tab lub Enter. Gdy to pole wyboru nie jest zaznaczone, inne znaki, takie jak kropka, przecinek, dwukropek, nawias otwierający i otwierający nawias klamrowy ({) również mogą dołączać instrukcje z wybranymi elementami.

## <a name="references"></a>Odwołania
 Można używać tych opcji, aby określać typy plików .js IntelliSense, które znajdują się w zakresie dla różnych typów projektów JavaScript. Odwołania IntelliSense są zazwyczaj używane do obsługi technologii IntelliSense dla obiektów globalnych. Można również użyć tej strony, aby ustawić kolejność ładowania skryptów, które muszą być ładowane w czasie wykonywania, oraz aby dodawać pliki rozszerzeń IntelliSense.

## <a name="uielement-list"></a>Lista elementów UI
 **Grupy odwołań**

 Ta opcja określa typ grupy odwołania. Obsługiwane są trzy grupy odwołań:

 Można używać wstępnie zdefiniowanych grup odwołań w celu określania, że konkretne pliki .js IntelliSense znajdują się w zakresie dla różnych projektów JavaScript. Dostępne są cztery grupy odniesień:

-   Niejawna (Windows *wersji*), dla [!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)] aplikacji przy użyciu języka JavaScript. Pliki zawarte w tej grupie znajdują się w zakresie dla każdego pliku .js otwartego w edytorze kodu dla [!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)] aplikacji przy użyciu języka JavaScript.

-   Niejawna (sieć Web) dla projektów HTML5. Pliki dołączone do tej grupy są w zakresie dla każdego pliku .js otwartego w Edytorze kodu dla tych typów projektu.

-   Grupy odniesienia dedykowanych procesów roboczych dla roboczych HTML5 sieci web. Pliki określone w tej grupie są w zakresie plików .js, które mają wyraźne odniesienie do grupy odwołań wyspecjalizowanych funkcji roboczych.

-   Ogólna dla innych typów projektów języka JavaScript.

**Dołączone pliki**

Ta opcja określa kolejność, w której pliki są ładowane do kontekstu usługi języka. Kolejność można skonfigurować za pomocą **Usuń**, **Przenieś w górę**, i **Przenieś w dół** przycisków. Aby technologia IntelliSense działała poprawnie, plik, który jest zależny od innego, musi być załadowany po pliku, od którego zależy.

> [!CAUTION]
> Jeśli obiekt jest zdefiniowany bezwarunkowo w dwóch lub więcej odwołań niejawnych, ostatnie odwołanie na tej liście będzie używane do określenia obiektu.


**Dodaj odwołanie do grupy**

Ta opcja umożliwia dodawanie dodatkowych plików .js IntelliSense przez przechodzenie do odpowiednich plików.

## <a name="see-also"></a>Zobacz też

- [Funkcja IntelliSense dla języka JavaScript](../../ide/javascript-intellisense.md)