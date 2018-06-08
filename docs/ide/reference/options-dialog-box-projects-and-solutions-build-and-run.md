---
title: Okno dialogowe Opcje, Projekty i rozwiązania, Kompilowanie i uruchamianie
ms.date: 07/14/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.Build_and_Run
- VS.ToolsOptionsPag.Projects.Build_and_Run
helpviewer_keywords:
- builds [Visual Studio], setting up
- run actions
- debugger, run options
ms.assetid: c884976e-c0df-4c6d-8e3a-856ea2bd547c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f6a569162105ffb577bdad854d973fff91b3c81b
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2018
ms.locfileid: "34845041"
---
# <a name="options-dialog-box-projects-and-solutions-build-and-run"></a>Okno dialogowe Opcje, Projekty i rozwiązania, Kompilowanie i uruchamianie

W tym oknie można określić maksymalną liczbę projektów Visual C++ lub C#, które można tworzyć w tym samym czasie, niektóre domyślne kompilacji zachowania i niektóre ustawienia dziennika kompilacji. Aby uzyskać dostęp do tych opcji, zaznacz **Narzędzia > Opcje** rozwiń **projekty i rozwiązania**i wybierz **skompilować i uruchomić**.

**Maksymalna liczba równoległych projektu kompilacji**

Określa maksymalną liczbę projektów Visual C++ i C#, które można tworzyć w tym samym czasie. Aby zoptymalizować proces kompilacji, maksymalną liczbę równolegle kompilowanych projektów jest automatycznie ustawiana liczby procesorów komputera. Wartość maksymalna to 32.

**Tworzyć tylko projekty startowe i zależności przy uruchomieniu**

Tworzy tylko projekt startowy i jego zależności użycia klucza, wybierz opcję F5 **debugowania > Start** polecenia menu lub odpowiednich poleceń na **kompilacji** menu. Jeżeli wyczyszczone, wszystkie projekty i zależności są kompilacji.

**Przy starcie, gdy projekty są nieaktualne**

*Dotyczy [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] tylko projekty.*

Podczas uruchamiania projektu z F5 lub **debugowania > Start** polecenia domyślne ustawienie **Monituj o kompilacji** wyświetla komunikat, jeśli konfiguracja projektu jest nieaktualny. Wybierz **kompilacji zawsze** Aby skompilować projekt, za każdym razem, gdy jest uruchomiony. Wybierz **nigdy nie kompilacji** Aby pominąć wszystkie kompilacje automatyczne uruchomienie projektu.

**Przy starcie, gdy kompilacji lub występują błędy wdrażania**

*Dotyczy [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] tylko projekty.*

Podczas uruchamiania projektu z F5 lub **debugowania > Start** polecenia domyślne ustawienie **Prompt uruchomić** wyświetla komunikat, jeśli projekt powinny być uruchamiane, nawet jeśli kompilacja nie powiodła się. Wybierz **uruchamiania starej wersji** do automatycznego uruchomienia ostatniego dobra kompilacja, co może spowodować niezgodność między uruchomiony kod i kod źródłowy. Wybierz **nie uruchamiaj** do Pomiń komunikat.

**Dla nowych rozwiązań Użyj obecnie wybranego projektu jako projekt startowy**

Gdy ta opcja jest ustawiona, nowych rozwiązań Użyj obecnie wybranego projektu jako projekt startowy.

**Szczegółowości danych wyjściowych kompilacji projektu programu MSBuild**

Określa, ile informacji jest wyświetlana w **dane wyjściowe** okna dla kompilacji.

**Poziom szczegółowości pliku dziennika MSBuild projektu kompilacji**

*Dotyczy [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] tylko projekty.*

Określa, ile informacje są zapisywane w pliku dziennika kompilacji, który znajduje się pod adresem \\... \\ *ProjectName*\Debug\\*ProjectName*. dziennika.

## <a name="see-also"></a>Zobacz także

- [Kompilowanie i tworzenie](../../ide/compiling-and-building-in-visual-studio.md)
- [Okno dialogowe Opcje, projekty i rozwiązania](projects-and-solutions-options-dialog-box.md)
- [Okno dialogowe Opcje, projekty i rozwiązania, projekty sieci Web](options-dialog-box-projects-and-solutions-web-projects.md)