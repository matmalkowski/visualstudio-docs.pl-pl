---
title: Weryfikowanie i debugowanie kodu aplikacji programu SharePoint | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- unit testing [SharePoint development in Visual Studio]
- IntelliTrace [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, IntelliTrace
- SharePoint development in Visual Studio, unit testing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7b5508fc1e1e663ffc6af17316f698ca5f2e13dd
ms.sourcegitcommit: 269b55b413d2c82e6aa56c6ab8e53da7926fb2e8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2018
ms.locfileid: "35237282"
---
# <a name="verifying-and-debugging-sharepoint-code"></a>Weryfikowanie i debugowanie kodu aplikacji programu SharePoint

Używając funkcji IntelliTrace i testów jednostkowych, można łatwiej debugować rozwiązania przeznaczone na platformę SharePoint i gwarantować poprawne działanie wszystkich zawartych w nich metod. Te funkcje można użyć dla projektów programu SharePoint w Visual Studio, wykonując te same procedury, podobnie jak w przypadku innych typów projektów.

## <a name="intellitrace"></a>IntelliTrace

Za pomocą funkcji IntelliTrace można określić nie tylko bieżący stan swojego rozwiązania programu SharePoint, ale także zdarzeń, które wystąpiły w przeszłości, oraz kontekstu, w którym miały one miejsce. W rozwiązaniu programu SharePoint można przechodzić do przodu i z powrotem w różne punkty w czasie, gdzie zostały zarejestrowane określone zdarzenia, oraz przeglądać stany i wartości zmiennych w każdym z tych punktów. Za pomocą tej dynamicznej nawigacji można szybciej i łatwiej debugować rozwiązania programu SharePoint bez konieczności ustawiania licznych punktów przerwania. Można również zapisać sesji debugowania IntelliTrace pliku dziennika (.iTrace), otwórz ją później w Visual Studio Enterprise i wykonać po crash debugowania. Pliku .iTrace zawiera szczegółowe informacje na temat określonych błędów SharePoint się stało, kiedy i gdzie, dzięki czemu można łatwiej ustalić przyczynę błędów. Informacje zawarte w pliku .iTrace są podzbiorem pełnego dziennika błędów tworzonego przez ujednolicony system protokołowania (Unified Logging System, ULS) w programie SharePoint. Wśród tych informacji są zdarzenia specyficzne dla programu SharePoint, np. otwarcie lub zamknięcie profilu użytkownika oraz załadowanie, odczyt i modyfikacja właściwości projektu programu SharePoint. Można określić, które zdarzenia funkcja IntelliTrace ma rejestrować. Aby uzyskać więcej informacji, zobacz [Using zapisywane są dane funkcji IntelliTrace](../debugger/using-saved-intellitrace-data.md).

Gdy w programie SharePoint wystąpi błąd, w oknie dialogowym tego błędu pojawia się „identyfikator korelacji”. Identyfikatory korelacji można również odczytywać ze zdarzeń wymienionych w pliku .iTrace. Aby wyświetlić listę wszystkich zdarzeń, które wystąpiły z Identyfikatorem korelacji danego, możesz wprowadzić identyfikator w **analizy** części strony Podsumowanie funkcji IntelliTrace. W sekcji można wskazać, czy mają być wyświetlane tylko nazwy zaistniałych zdarzeń czy też nazwy razem z informacjami o wywołaniach, takimi jak nazwy funkcji, punkty wejścia i wyjścia, parametry i zwracane wartości.

Zdarzenia programu Visual Studio można uzyskać w funkcji IntelliTrace, wybierając **F5** klucza. Jednak w przypadku zdarzeń specyficznych dla programu SharePoint do zbierania danych funkcji IntelliTrace w rozwiązaniach programu SharePoint należy używać programu Microsoft Monitoring Agent. Narzędzie gromadzi dane funkcji IntelliTrace i tworzy pliki .iTrace dla aplikacji wdrożonych poza programem Visual Studio. Aby uzyskać więcej informacji, zobacz [funkcji IntelliTrace](../debugger/intellitrace-features.md) i [przy użyciu autonomicznego modułu zbierającego IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md).

## <a name="unit-testing"></a>Testowanie jednostkowe

Ułatwieniem przy wyszukiwaniu błędów w kodzie są testy jednostkowe, ponieważ można w nich zapisać kod testów i wykonywać go wewnątrz metod testowych. Metody te zawierają puste zmienne oraz instrukcję Assert, za pomocą której można weryfikować logikę i funkcjonalność projektu w oparciu o model obiektów programu SharePoint. Aby uzyskać więcej informacji, zobacz [swój kod testu jednostkowego](../test/unit-test-your-code.md).

### <a name="support-for-microsoft-fakes-framework"></a>Obsługa Microsoft Fakes Framework

Projekty programu SharePoint obsługują Microsoft Fakes. To środowisko izolacji, w którym można tworzyć oparte na delegatach zastępcze klasy i podkładki testowe w aplikacjach bazujących na środowisku .NET Framework. Środowisko Fakes pozwala generować, obsługiwać i wprowadzać fikcyjne implementacje do testów jednostkowych. Zastępcze klasy i podkładki odizolowują testy jednostkowe od środowiska. Zastępcze klasy umożliwiają testowanie kodu, który wykorzystuje interfejsy lub niezapieczętowane klasy z metodami możliwymi do zastąpienia. Z kolei podkładki umożliwiają przekierowywanie ustalonych wywołań do zapieczętowanych klas z metodami statycznymi lub niedającymi się zastąpić do alternatywnymi implementacji podkładek. Delegaci z typami zastępczych klas i typami podkładek umożliwiają dynamiczne dostosowywanie zachowań poszczególnych elementów członkowskich takich zastępczych klas. Aby uzyskać więcej informacji, zobacz [izolowanie kodu w obszarze testów z Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md).

## <a name="related-articles"></a>Pokrewne artykuły

|Tytuł|Opis|
|-----------|-----------------|
|[IntelliTrace](../debugger/intellitrace.md)|Opis sposobów łatwiejszego debugowania rozwiązań programu Visual Studio za pomocą funkcji IntelliTrace.|
|[Przewodnik: Debugowanie aplikacji SharePoint przy użyciu narzędzia IntelliTrace](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md)|Wyjaśnienie, jak znaleźć błędy kodu w projekcie programu SharePoint przy użyciu funkcji IntelliTrace.|
|[Testowanie jednostek kodu](../test/unit-test-your-code.md)|Opisuje sposób wyszukiwania logiki błędów w kodzie za pomocą testów jednostkowych.|

## <a name="see-also"></a>Zobacz także

- [Podnoszenie jakości kodu](../test/improve-code-quality.md)