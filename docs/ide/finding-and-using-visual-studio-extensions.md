---
title: "Znajdowanie i korzystanie z rozszerzeń programu Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 06/07/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.ExtensionManager
helpviewer_keywords:
- install extensions
- install packages
- managing extensions visual studio
ms.assetid: 4ca92d93-31b9-47ef-8109-4a429d9e2ca3
caps.latest.revision: "42"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0327ccaa52f3bd348246eea39b754f5c9069f3a1
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2017
---
# <a name="finding-and-using-visual-studio-extensions"></a>Znajdowanie rozszerzeń programu Visual Studio i korzystanie z nich
Rozszerzenia programu Visual Studio są pakiety kodu umożliwiające działanie w programie Visual Studio i udostępnia nowe i ulepszone funkcje programu Visual Studio. Więcej informacji na temat rozszerzeń programu Visual Studio w tym miejscu można znaleźć: [programu Visual Studio SDK](../extensibility/visual-studio-sdk.md).  

 Można użyć **rozszerzenia i aktualizacje** okno dialogowe, aby zainstalować rozszerzenia programu Visual Studio i przykłady z witryny sieci Web i innych lokalizacjach, a następnie włączyć, wyłączyć, zaktualizować lub je odinstalować. (**Narzędzia / rozszerzenia i aktualizacje**, lub typ **rozszerzenia** w **Szybkie uruchamianie** okno). Okno dialogowe zawiera również aktualizacje zainstalowane przykłady i rozszerzenia. Można również pobrać z witryny sieci Web rozszerzenia lub pobrać je z innymi deweloperami.  

> [!NOTE]
>  Począwszy od programu Visual Studio 2015 rozszerzenia hostowanych w programie Visual Studio Marketplace zostanie automatycznie zaktualizowana.  Możesz zmienić to ustawienie za pomocą **rozszerzenia i aktualizacje** okna dialogowego.  Zobacz sekcję dotyczącą **aktualizacje automatyczne rozszerzenia** poniżej szczegółowe informacje.  

## <a name="finding-visual-studio-extensions"></a>Znajdowanie rozszerzeń programu Visual Studio  
 Można zainstalować rozszerzenia z [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). Rozszerzeniami mogą być formanty, przykłady, szablony, narzędzia lub inne składniki, które dodają nowe funkcjonalności do programu Visual Studio. Program Visual Studio obsługuje rozszerzenia w formacie pakietu VSIX — te obejmują szablony projektów, szablony, element **przybornika** elementów, składników zarządzanych rozszerzenia Framework (MEF) i VSPackages. Można również pobrać i zainstalować rozszerzenia na podstawie MSI, ale **rozszerzenia i aktualizacje** okno dialogowe nie może włączyć lub wyłączyć je. Visual Studio Marketplace zawiera rozszerzenia VSIX jak również MSI.  

## <a name="installing-or-uninstalling-visual-studio-extensions"></a>Instalowanie lub odinstalowywanie rozszerzenia programu Visual Studio  
 W **rozszerzenia i aktualizacje**, znaleźć rozszerzenia, które chcesz zainstalować. (Jeśli znasz nazwę lub część nazwy rozszerzenia można przeszukiwać w **wyszukiwania** okna.) Kliknij przycisk **Pobierz**.  Rozszerzenie zostanie zaplanowane do zainstalowania. Rozszerzenie zostanie zainstalowane po zamknięciu wszystkich wystąpień programu Visual Studio.

 Podczas próby instalacji rozszerzenia, które ma zależności, instalator sprawdza, czy są one już zainstalowane. Jeśli nie są one zainstalowane, **rozszerzenia i aktualizacje** okno dialogowe zawiera listę zależności, które należy zainstalować przed zainstalowaniem rozszerzenia.  

 Jeśli nie chcesz już dłużej używać rozszerzenia, możesz je wyłączyć lub odinstalować. Wyłączone rozszerzenie jest wciąż zainstalowane, ale nie jest załadowane. Można wyłączyć tylko rozszerzenia VSIX; rozszerzenia, które zostały zainstalowane przy użyciu Instalatora MSI tylko mogła zostać usunięta. Znaleźć rozszerzenia, a następnie kliknij przycisk **Odinstaluj** lub **wyłączyć**. Aby zwolnić wyłączono rozszerzenie, należy ponownie uruchomić program Visual Studio.  

## <a name="per-user-and-administrative-extensions"></a>Rozszerzenia administracyjne i dla poszczególnych użytkowników  
 Większość rozszerzenia są rozszerzenia dla poszczególnych użytkowników i są zainstalowane w **%LocalAppData%\Microsoft\VisualStudio\\< wersji programu Visual Studio\>\Extensions\\**  folderu. Kilka rozszerzeń są rozszerzenia administracyjnych i są zainstalowane w  **\<folder instalacji programu Visual Studio > \Common7\IDE\Extensions\\**  folderu.  

 Aby chronić komputer przed rozszerzeń, które mogą zawierać błędy lub złośliwy kod, można ograniczyć rozszerzenia dla poszczególnych użytkowników można załadować tylko wtedy, gdy program Visual Studio jest uruchamiana z normalnymi uprawnieniami użytkownika. Oznacza to, że rozszerzenia użytkownika są wyłączone, po uruchomieniu programu Visual Studio z uprawnieniami administracyjnymi. Aby to zrobić, przejdź do **rozszerzenia i aktualizacje** strona Opcje (**narzędzia / Opcje**, **środowiska**, **rozszerzenia i aktualizacje**, lub po prostu Typ **rozszerzenia** w **Szybkie uruchamianie** okno). Wyczyść **obciążenia rozszerzeń dla poszczególnych użytkowników w przypadku uruchamiania jako administrator** pole wyboru, a następnie uruchom ponownie program Visual Studio.  

## <a name="automatic-extension-updates"></a>Aktualizacje automatyczne rozszerzenia  
 Rozszerzenia dla poszczególnych użytkowników są automatycznie aktualizowane nowa wersja jest dostępna dla programu Visual Studio Marketplace.  Nowa wersja rozszerzenia jest wykryte i zainstalowane w tle i po następnym ponownym uruchomieniu programu Visual Studio, nowa wersja rozszerzenia będą działać.  

 Tylko rozszerzenia dla poszczególnych użytkowników mogą być automatycznie aktualizowane.  Rozszerzenia administracyjne, które są instalowane dla wszystkich użytkowników nie będzie aktualizowana i nadal ręcznie zainstalować nowe wersje za pośrednictwem **rozszerzenia i aktualizacje** okna dialogowego **aktualizacje** węzła. Widać, które rozszerzenia zostanie automatycznie zaktualizowana w okienku szczegółów rozszerzenia **rozszerzenia i aktualizacje** okna dialogowego.  

 Jeśli chcesz wyłączyć aktualizacje automatyczne, należy wyłączyć funkcję dla wszystkich rozszerzeń lub tylko określonego rozszerzenia.  

-   Aby wyłączyć aktualizacje automatyczne dla wszystkich rozszerzeń, wybierz **zmiany ustawień rozszerzenia i aktualizacje** łącze w **rozszerzenia i aktualizacje** okna dialogowego i usuń zaznaczenie pola wyboru **automatycznie Aktualizuj rozszerzenia**.  

-   Aby wyłączyć automatyczne aktualizacje dla określonego rozszerzenia, usuń zaznaczenie pola wyboru **automatycznie Aktualizuj to rozszerzenie** opcji w okienku szczegółów rozszerzenia w prawej części **rozszerzenia i aktualizacje** okna dialogowego.  

> [!NOTE]
>  Począwszy od programu Visual Studio 2015 Update 2, można określić (w **narzędzia / Opcje / środowiska / rozszerzenia i aktualizacje**) czy będzie aktualizacji automatycznych dla rozszerzeń dla poszczególnych użytkowników, wszystkie rozszerzenia użytkownika lub obu (ustawienie domyślne).  

## <a name="extension-crash-notifications"></a>Rozszerzenie awarii powiadomienia

W Visual Studio 2017 r (wersja 15 ustęp 3 — wersja zapoznawcza) programu Visual Studio powiadamia użytkownika, jeśli podejrzewa, że rozszerzenie uczestniczyła w awarii podczas poprzedniej sesji. Visual Studio ulega awarii, są przechowywane stosu wyjątku. Przy następnym uruchomieniu programu Visual Studio sprawdza stosu, począwszy od liścia i działają na bazie. Jeśli Visual Studio Określa, że ramka należy moduł, który jest częścią zainstalowane i włączone rozszerzenie, powiadomi użytkownika o wiadomości, takie jak

  "Poprzedniej sesji został nieoczekiwanie zakończony. Wyłączanie rozszerzenia "extension_name" może zapobiec podobne problemy."

Można zignorować powiadomienie lub wykonać jedną z następujących czynności:

-   Wybierz **wyłącza to rozszerzenie**. Visual Studio wyłącza rozszerzenia i informuje o tym, czy należy ponownie uruchomić system, aby wyłączyć zaczęły obowiązywać. Można ponownie włączyć rozszerzenia w **rozszerzenia i aktualizacje** okno dialogowe, jeśli chcesz.

-   Wybierz **nie pokazuj więcej dla tego rozszerzenia**. IDE nie będą już wyświetlane powiadomienia o awarii (Crash) skojarzony z tym rozszerzeniem, ale zostanie ona Pokaż powiadomienia o awarii skojarzone z innymi rozszerzeniami.

-   Wybierz **więcej** do wyświetlania tego tematu pomocy w domyślnej przeglądarce.

-   Wybierz **X** przycisk na końcu powiadomień na odrzucenie powiadomienia. Jeśli to samo rozszerzenie jest związany z awarii w przyszłych sesji, ponownie zostanie wyświetlone powiadomienie.

> [!NOTE]
>  Powiadomienie o awarii oznacza, że tylko spośród modułów rozszerzenia znajdowała się na stosie dla tej awarii. Nie musi to oznaczać, że rozszerzenie sam spowodował awarię (crash). Istnieje możliwość rozszerzenia wywołuje kod, który wchodzi w skład programu Visual Studio, czy kod spowodował awarię (crash). Jednak powiadomienia nadal może być przydatne w przypadku scenariuszy, które doprowadziło do awarii nie jest dla Ciebie ważne. W takim przypadku wyłączenie rozszerzenia pozwala uniknąć w przyszłości tego samego awarii bez wywierania wpływu na wydajność.


## <a name="sample-master-copies-and-working-copies"></a>Przykładowy wzorzec kopii i Praca z kopii  
 Po zainstalowaniu przykładu online, rozwiązanie jest przechowywane w dwóch miejscach:  

-   Kopia robocza są przechowywane w lokalizacji określonej w **nowy projekt** okno dialogowe.  

-   Oddzielna kopia główna jest przechowywana na komputerze.  

 Można użyć **rozszerzenia i aktualizacje** okno dialogowe, aby wykonać te zadania związane z próbek:  

-   Wypisanie listy kopii głównych przykładów, które zostały zainstalowane.  

-   Wyłączenie lub odinstalowanie kopii głównej przykładu.  

-   Zainstalowanie pakietów przykładów, które są zbiorami przykładów odnoszących się do technologii lub funkcji.  

-   Instalowanie pojedynczych przykładów online. (Można to również zrobić w **nowy projekt** okno dialogowe.)  

-   Wyświetlanie powiadomień o aktualizacjach, gdy zostaną opublikowane zmiany kodu źródłowego dla zainstalowanych przykładów.  

-   Zaktualizuj kopii głównej próbki zainstalowane po powiadomienie o aktualizacji.  

## <a name="installing-without-using-the-extensions-and-updates-dialog-box"></a>Instalowanie bez używania okna dialogowego Rozszerzenia i aktualizacje  
 Rozszerzenia, które zostały opakowane w plikach .vsix mogą być dostępne w lokalizacji innej niż Visual Studio Marketplace. **Rozszerzenia i aktualizacje** okno dialogowe nie może wykryć te pliki, ale można zainstalować pliku .vsix przez dwukrotne kliknięcie pliku, lub wybierając pliku i naciskając klawisz ENTER. Następnie postępuj zgodnie z instrukcjami. Jeśli rozszerzenie jest zainstalowane, możesz użyć **rozszerzenia i aktualizacje** okno dialogowe, aby ją włączyć, wyłączyć lub ją odinstalować.  

## <a name="extension-types-not-supported-by-the-extensions-and-updates-dialog-box"></a>Typy rozszerzeń, które nie są obsługiwane przez rozszerzenia i aktualizacje — okno dialogowe  
 Visual Studio w dalszym ciągu obsługuje rozszerzenia, które są instalowane przez Instalator (MSI) programu Microsoft ale nie za pomocą **rozszerzenia i aktualizacje** okno dialogowe bez żadnych modyfikacji.  

> [!TIP]
>  Jeśli rozszerzenie na podstawie MSI zawiera plik extension.vsixmanifest, rozszerzenie jest obecne w **rozszerzenia i aktualizacje** okno dialogowe.
