---
title: Ustawienia projektu VC ++, projekty i rozwiązania, okno dialogowe Opcje | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Projects.VCBuild
helpviewer_keywords:
- builds [Visual Studio], logs
- build process [C++]
- files [Visual Studio], built by C/C++ compiler
- file extensions, built by C or C++ compiler
- cl.exe compiler, file extensions
- extensions, files built by C or C++ compiler
- BuildLog.htm
ms.assetid: 56420efd-6a95-464e-b890-e2b38c48d66a
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8b6f588a1361c9184b67e510688128f621754f82
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42629909"
---
# <a name="vc-project-settings-projects-and-solutions-options-dialog-box"></a>Ustawienia projektu VC++, projekty i rozwiązania, opcje — Okno dialogowe
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [ustawienia projektu VC ++, projekty i rozwiązania, okno dialogowe Opcje](https://docs.microsoft.com/visualstudio/ide/reference/vcpp-project-settings-projects-and-solutions-options-dialog-box).  
  
  
To okno dialogowe pozwala zdefiniować [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] ustawienia związane z kompilacji, rejestrowanie i dodatkowe typy plików projektu.  
  
### <a name="to-access-this-dialog-box"></a>Dostęp do tego okna dialogowego  
  
1.  Na **narzędzia** menu, kliknij przycisk **opcje**.  
  
2.  Wybierz **projekty i rozwiązania**, a następnie wybierz pozycję **ustawienia projektu VC ++**.  
  
## <a name="build-customization-search-path"></a>Ścieżka wyszukiwania dostosowania kompilacji  
 Określa listę katalogów, które zawierają pliki Rules, które ułatwiają definiowanie reguł kompilacji dla Twoich projektów.  
  
## <a name="build-logging"></a>Rejestrowanie kompilacji  
 **Tak**  
 Włącza generowanie pliku dziennika kompilacji. Ta opcja powoduje wygenerowanie nazwę BuildLog.htm, które znajdują się w katalogu pośrednie pliki projektu. Każdej nowej kompilacji zastępuje poprzedni plik nazwę BuildLog.htm.  
  
 **Brak**  
 Wyłącza generowanie pliku dziennika kompilacji.  
  
## <a name="build-timing"></a>Czas kompilacji  
 **Tak**  
 Włącza międzyczasy kompilacji. Jeśli zaznaczone, czas potrzebny na zakończenie kompilacji jest publikowany w oknie danych wyjściowych. Aby uzyskać więcej informacji, zobacz [okno danych wyjściowych](../../ide/reference/output-window.md).  
  
 **Brak**  
 Wyłącza międzyczasy kompilacji.  
  
## <a name="extensions-to-hide"></a>Ukryte rozszerzenia  
 Określa rozszerzenia nazw plików, które nie będą wyświetlane w **Eksploratora rozwiązań** podczas **Pokaż wszystkie pliki** jest włączona.  
  
## <a name="extensions-to-include"></a>Rozszerzenia do uwzględnienia  
 Określa rozszerzenia nazw plików, które mogą być przenoszone do projektu.  
  
## <a name="maximum-concurrent-c-compilations"></a>Maksymalna współbieżnych kompilacji języka C++  
 Określa maksymalną liczbę rdzeni Procesora używanych w równoległej kompilacji języka C++.  
  
## <a name="show-environment-in-log"></a>Pokaż środowisko w rejestrze  
 **Tak**  
 Wyświetla listę zmiennych środowiskowych w pliku dziennika kompilacji. Ta opcja określa, aby wyświetlić wszystkich systemowych zmiennych środowiskowych, podczas kompilacji z [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] projektów do kompilacji pliku dziennika.  
  
 **Brak**  
 Wyklucz zmienne środowiskowe z pliku dziennika kompilacji.  
  
## <a name="solution-explorer-mode"></a>Tryb Eksploratora rozwiązań  
 **Pokaż tylko pliki w projekcie**  
 Konfiguruje **Eksploratora rozwiązań** Aby wyświetlić tylko pliki w projekcie.  
  
 **Pokaż wszystkie pliki**  
 Konfiguruje **Eksploratora rozwiązań** Aby wyświetlić pliki w projekcie i pliki na dysku w folderze projektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilowanie programów C/C++](http://msdn.microsoft.com/library/fa6ed4ff-334a-4d99-b5e2-a1f83d2b3008)   
 [Dokumentacja kompilacji w języku C/C++](http://msdn.microsoft.com/library/100b4ccf-572c-4d1f-970c-fa0bc0cc0d2d)



