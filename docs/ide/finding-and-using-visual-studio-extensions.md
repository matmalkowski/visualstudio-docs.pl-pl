---
title: Znajdowanie i używanie rozszerzeń programu Visual Studio
ms.date: 06/07/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.ExtensionManager
helpviewer_keywords:
- install extensions
- install packages
- managing extensions visual studio
ms.assetid: 4ca92d93-31b9-47ef-8109-4a429d9e2ca3
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9a5b562aa6fe4a64f92d66ad0a6fff0395e5314a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="find-and-use-visual-studio-extensions"></a>Znajdowanie i używanie rozszerzeń programu Visual Studio

Rozszerzenia programu Visual Studio są pakiety kodu umożliwiające działanie w programie Visual Studio i udostępnia nowe i ulepszone funkcje programu Visual Studio. Więcej informacji na temat rozszerzeń programu Visual Studio w tym miejscu można znaleźć: [programu Visual Studio SDK](../extensibility/visual-studio-sdk.md).

Można użyć **rozszerzenia i aktualizacje** okno dialogowe, aby zainstalować rozszerzenia programu Visual Studio i przykłady z witryny sieci Web i innych lokalizacjach, a następnie włączyć, wyłączyć, zaktualizować lub je odinstalować. (**Narzędzia > rozszerzenia i aktualizacje**, lub typ **rozszerzenia** w **Szybkie uruchamianie** okno). Okno dialogowe zawiera również aktualizacje zainstalowane przykłady i rozszerzenia. Można również pobrać z witryny sieci Web rozszerzenia lub pobrać je z innymi deweloperami.

> [!NOTE]
> Począwszy od programu Visual Studio 2015 hostowanych w programie Visual Studio Marketplace rozszerzenia są automatycznie aktualizowane. Możesz zmienić to ustawienie za pomocą **rozszerzenia i aktualizacje** okna dialogowego.  Zobacz sekcję dotyczącą **aktualizacje automatyczne rozszerzenia** poniżej szczegółowe informacje.

## <a name="finding-visual-studio-extensions"></a>Znajdowanie rozszerzeń programu Visual Studio

Można zainstalować rozszerzenia z [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). Rozszerzeniami mogą być formanty, przykłady, szablony, narzędzia lub inne składniki, które dodają nowe funkcjonalności do programu Visual Studio. Program Visual Studio obsługuje rozszerzenia w formacie pakietu VSIX — te obejmują szablony projektów, szablony, element **przybornika** elementów, składników zarządzanych rozszerzenia Framework (MEF) i VSPackages. Można również pobrać i zainstalować rozszerzenia na podstawie MSI, ale **rozszerzenia i aktualizacje** okno dialogowe nie może włączyć lub wyłączyć je. Visual Studio Marketplace zawiera rozszerzenia VSIX jak również MSI.

## <a name="installing-or-uninstalling-visual-studio-extensions"></a>Instalowanie lub odinstalowywanie rozszerzenia programu Visual Studio

W **rozszerzenia i aktualizacje**, znaleźć rozszerzenia, które chcesz zainstalować. (Jeśli znasz nazwę lub część nazwy rozszerzenia można przeszukiwać w **wyszukiwania** okna.) Kliknij przycisk **Pobierz**.  Rozszerzenie zostanie zaplanowane do zainstalowania. Rozszerzenie zostanie zainstalowane po zamknięciu wszystkich wystąpień programu Visual Studio.

Podczas próby instalacji rozszerzenia, które ma zależności, instalator sprawdza, czy są one już zainstalowane. Jeśli nie są one zainstalowane, **rozszerzenia i aktualizacje** okno dialogowe zawiera listę zależności, które należy zainstalować przed zainstalowaniem rozszerzenia.

Jeśli nie chcesz już dłużej używać rozszerzenia, możesz je wyłączyć lub odinstalować. Wyłączone rozszerzenie jest wciąż zainstalowane, ale nie jest załadowane. Można wyłączyć tylko rozszerzenia VSIX; rozszerzenia, które zostały zainstalowane przy użyciu Instalatora MSI tylko mogła zostać usunięta. Znaleźć rozszerzenia, a następnie kliknij przycisk **Odinstaluj** lub **wyłączyć**. Aby zwolnić wyłączono rozszerzenie, należy ponownie uruchomić program Visual Studio.

## <a name="per-user-and-administrative-extensions"></a>Dla poszczególnych użytkowników i rozszerzenia administracyjne

Większość rozszerzenia są rozszerzenia dla poszczególnych użytkowników i są zainstalowane w *%LocalAppData%\Microsoft\VisualStudio\\< wersji programu Visual Studio\>\Extensions\\*  folderu. Kilka rozszerzeń są rozszerzenia administracyjnych i są zainstalowane w *\<folder instalacji programu Visual Studio > \Common7\IDE\Extensions\\* folderu.

Aby chronić komputer przed rozszerzeń, które mogą zawierać błędy lub złośliwy kod, można ograniczyć rozszerzenia dla poszczególnych użytkowników można załadować tylko wtedy, gdy program Visual Studio jest uruchamiana z normalnymi uprawnieniami użytkownika. Oznacza to, że rozszerzenia użytkownika są wyłączone, po uruchomieniu programu Visual Studio z uprawnieniami administracyjnymi. Aby to zrobić, przejdź do **rozszerzenia i aktualizacje** strona Opcje (**Narzędzia > Opcje** > **środowiska** > **rozszerzeń Aktualizacje i**, lub po prostu wpisz **rozszerzenia** w **Szybkie uruchamianie** okno). Wyczyść **obciążenia rozszerzeń dla poszczególnych użytkowników w przypadku uruchamiania jako administrator** pole wyboru, a następnie uruchom ponownie program Visual Studio.

## <a name="automatic-extension-updates"></a>Aktualizacje automatyczne rozszerzenia

Rozszerzenia dla poszczególnych użytkowników są automatycznie aktualizowane nowa wersja jest dostępna dla programu Visual Studio Marketplace.  Nowa wersja rozszerzenia jest wykryte i zainstalowane w tle i po następnym ponownym uruchomieniu programu Visual Studio, nowa wersja rozszerzenia będą działać.

Tylko rozszerzenia dla poszczególnych użytkowników mogą być automatycznie aktualizowane.  Rozszerzenia administracyjne, które są instalowane dla wszystkich użytkowników nie będzie aktualizowana i nadal ręcznie zainstalować nowe wersje za pośrednictwem **rozszerzenia i aktualizacje** okna dialogowego **aktualizacje** węzła. Widać, które rozszerzenia zostanie automatycznie zaktualizowana w okienku szczegółów rozszerzenia **rozszerzenia i aktualizacje** okna dialogowego.

Jeśli chcesz wyłączyć aktualizacje automatyczne, należy wyłączyć funkcję dla wszystkich rozszerzeń lub tylko określonego rozszerzenia.

- Aby wyłączyć aktualizacje automatyczne dla wszystkich rozszerzeń, wybierz **zmiany ustawień rozszerzenia i aktualizacje** łącze w **rozszerzenia i aktualizacje** okna dialogowego i usuń zaznaczenie pola wyboru **automatycznie Aktualizuj rozszerzenia**.

- Aby wyłączyć automatyczne aktualizacje dla określonego rozszerzenia, usuń zaznaczenie pola wyboru **automatycznie Aktualizuj to rozszerzenie** opcji w okienku szczegółów rozszerzenia w prawej części **rozszerzenia i aktualizacje** okna dialogowego.

> [!NOTE]
> Począwszy od programu Visual Studio 2015 Update 2, można określić (w **Narzędzia > Opcje > środowiska > rozszerzenia i aktualizacje**) czy będzie aktualizacji automatycznych dla rozszerzeń dla poszczególnych użytkowników, wszystkie rozszerzenia użytkownika lub obu (wartość domyślna ustawienie).

## <a name="extension-crashunresponsiveness-notifications"></a>Rozszerzenie awarii/odpowiadać powiadomienia

Nowość w **programu Visual Studio 2017 wersji 15 ustęp 3**, Visual Studio powiadamia użytkownika, jeśli podejrzewa, że rozszerzenie uczestniczyła w awarii podczas poprzedniej sesji. Visual Studio ulega awarii, są przechowywane stosu wyjątku. Przy następnym uruchomieniu programu Visual Studio sprawdza stosu, począwszy od liścia i działają na bazie. Jeśli program Visual Studio Określa, że ramki należy moduł, który jest częścią zainstalowane i włączone rozszerzenie, pokazuje powiadomienie.

Nowość w **programu Visual Studio 2017 wersji 15,6**, Visual Studio również powiadamia użytkownika, jeśli podejrzewa, powoduje rozszerzenie interfejsu użytkownika przestanie odpowiadać.

Gdy te powiadomienia są wyświetlane, możesz zignorować powiadomienie lub wykonać jedną z następujących czynności:

- Wybierz **wyłącza to rozszerzenie**. Visual Studio wyłącza rozszerzenia i informuje o tym, czy należy ponownie uruchomić system, aby wyłączyć zaczęły obowiązywać. Można ponownie włączyć rozszerzenia w **rozszerzenia i aktualizacje** okno dialogowe, jeśli chcesz.

- Wybierz **nigdy nie pokazuj więcej tego komunikatu**.
  - Jeśli powiadomienia dotyczą awarii w poprzedniej sesji, Visual Studio nie będą już wyświetlane się, że występuje powiadomienie po awarii, skojarzony z tym rozszerzeniem. Visual Studio będzie widoczna powiadomienia w przypadku braku odpowiedzi może być skojarzony z tym rozszerzeniem lub awarii lub brak reakcji, które mogą być skojarzone z innymi rozszerzeniami.
  - Jeśli powiadomienia dotyczą braku odpowiedzi, IDE nie będą już wyświetlane powiadomienie po to rozszerzenie jest skojarzony z braku odpowiedzi. Visual Studio będzie widoczna powiadomień dotyczące awarii dla tego rozszerzenia i związane z awarii i braku odpowiedzi powiadomienia dla innych rozszerzeń.

- Wybierz **więcej** przejdzie do tej strony.

- Wybierz **X** przycisk na końcu powiadomień na odrzucenie powiadomienia. Nowe powiadomienie będzie wyświetlany dla przyszłych wystąpień rozszerzenia skojarzona z awaria lub brak reakcji interfejsu użytkownika.

> [!NOTE]
> Powiadomienie nie odpowiadać lub awarii interfejsu użytkownika oznacza tylko że jeden z modułów rozszerzenia na stosie gdy odpowiadać interfejsu użytkownika lub w przypadku wystąpienia awarii. Nie musi to oznaczać, że rozszerzenie sam był dziedziczonej z istotnymi elementami. Istnieje możliwość, że rozszerzenie o nazwie kodu, który wchodzi w skład programu Visual Studio, co z kolei spowodowało odpowiadać interfejsu użytkownika lub awarii. Jednak powiadomienia nadal mogą być przydatne, jeśli rozszerzenie, które doprowadziły do awarii lub brak reakcji interfejsu użytkownika nie jest dla Ciebie ważne. W takim przypadku wyłączenie rozszerzenia pozwala uniknąć braku odpowiedzi interfejsu użytkownika lub awarii w przyszłości, bez wywierania wpływu na wydajność.

## <a name="sample-master-copies-and-working-copies"></a>Przykład kopii wzorca i kopie robocze

Po zainstalowaniu przykładu online, rozwiązanie jest przechowywane w dwóch miejscach:

- Kopia robocza są przechowywane w lokalizacji określonej w **nowy projekt** okno dialogowe.

- Oddzielna kopia główna jest przechowywana na komputerze.

Można użyć **rozszerzenia i aktualizacje** okno dialogowe, aby wykonać te zadania związane z próbek:

- Wypisanie listy kopii głównych przykładów, które zostały zainstalowane.

- Wyłączenie lub odinstalowanie kopii głównej przykładu.

- Zainstalowanie pakietów przykładów, które są zbiorami przykładów odnoszących się do technologii lub funkcji.

- Instalowanie pojedynczych przykładów online. (Można to również zrobić w **nowy projekt** okno dialogowe.)

- Wyświetlanie powiadomień o aktualizacjach, gdy zostaną opublikowane zmiany kodu źródłowego dla zainstalowanych przykładów.

- Zaktualizuj kopii głównej próbki zainstalowane po powiadomienie o aktualizacji.

## <a name="installing-without-using-the-extensions-and-updates-dialog-box"></a>Instalowanie bez za pomocą okna dialogowego rozszerzenia i aktualizacje

Rozszerzenia, które zostały opakowane w *.vsix* pliki mogą być dostępne w lokalizacji innej niż Visual Studio Marketplace. **Rozszerzenia i aktualizacje** okno dialogowe nie może wykryć te pliki, ale można zainstalować *.vsix* pliku, klikając dwukrotnie plik, lub zaznacz ją i naciskając klawisz **Enter**klucza. Następnie postępuj zgodnie z instrukcjami. Jeśli rozszerzenie jest zainstalowane, możesz użyć **rozszerzenia i aktualizacje** okno dialogowe, aby ją włączyć, wyłączyć lub ją odinstalować.

## <a name="extension-types-not-supported-by-the-extensions-and-updates-dialog-box"></a>Typy rozszerzeń, które nie są obsługiwane w oknie dialogowym rozszerzenia i aktualizacje

Visual Studio w dalszym ciągu obsługuje rozszerzenia, które są instalowane przez Instalator (MSI) programu Microsoft ale nie za pomocą **rozszerzenia i aktualizacje** okno dialogowe bez żadnych modyfikacji.

> [!TIP]
> Jeśli na podstawie MSI rozszerzenie zawiera *extension.vsixmanifest* rozszerzenia plików, będą wyświetlane w **rozszerzenia i aktualizacje** okno dialogowe.