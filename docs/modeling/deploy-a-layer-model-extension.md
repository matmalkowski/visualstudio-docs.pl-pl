---
title: Wdrażanie rozszerzenia modelu warstwy
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, deploying extensions
- layer models, deploying extensions
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 0ec537ec070188c967c2db02548cf487180c0bae
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="deploy-a-layer-model-extension"></a>Wdrażanie rozszerzenia modelu warstwy
Innych użytkowników programu Visual Studio można zainstalować warstwę modelowania rozszerzeń, które można utworzyć za pomocą programu Visual Studio.

## <a name="installing-your-extension"></a>Instalowanie rozszerzenia
 Rozszerzenie jest kompilowana w pliku VSIX, które można zainstalować na innych komputerach. Można także zainstalować na komputerze deweloperskim, aby udostępnić rozszerzenia w głównym wystąpienie programu Visual Studio.

#### <a name="to-install-the-extension"></a>Aby zainstalować to rozszerzenie

1.  W projekcie, który zawiera **source.vsix.manifest**, otwórz **bin\\ \***  w Eksploratorze plików.

2.  Kopiuj  **\*.vsix** plik na komputerze, na którym chcesz zainstalować rozszerzenia.

3.  Na komputerze docelowym kliknij dwukrotnie plik *.vsix w Eksploratorze Windows.

     Otwiera Instalatora VSIX.

#### <a name="to-uninstall-the-extension"></a>Aby odinstalować rozszerzenia

1.  W programie Visual Studio na **narzędzia** menu, kliknij przycisk **rozszerzenia i aktualizacje**.

2.  Kliknij nazwę rozszerzenia, a następnie kliknij przycisk **Odinstaluj**.

## <a name="installing-an-extension-on-a-team-foundation-build-server"></a>Instalowanie rozszerzenia na serwerze Team Foundation Build
 [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] serwery nie mają zwykle zainstalowanego programu Visual Studio, a więc nie można zainstalować pliku VSIX, kliknij go dwukrotnie. Instalacja [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] zawiera niektóre składniki umożliwiające rozszerzenie VSIX uruchomić, ale należy ręcznie zainstalować rozszerzenie.

#### <a name="to-install-your-layer-extension-on-a-includeesprbuildmiscincludesesprbuildmdmd-server"></a>Aby zainstalować rozszerzenie warstwy na [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] serwera

1.  Kopiuj **.vsix** pliki na komputerze projektowym do [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] komputera.

     Umieść plik VSIX w jednym z następujących lokalizacji:

    -   Aby zainstalować dla wszystkich użytkowników i usług:

         %ProgramFiles%\Microsoft visual Studio [wersja] \Common7\IDE\Extensions\Microsoft

    -   Aby zainstalować tylko w przypadku usługi sieciowej, która uruchamia [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)]:

         %WinDir%\ServiceProfiles\NetworkService\AppData\Local\Microsoft\VisualStudio\\[version]\Extensions\Microsoft

    -   Jeśli skonfigurowano [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] do uruchamiania w trybie interakcyjnym jako określony użytkownik, można zainstalować tylko dla tego użytkownika:

         %LocalAppData%\Microsoft\VisualStudio\\[version]\Extensions\Microsoft

        > [!NOTE]
        >  % LocalAppData % jest zwykle *DriveName*: Użytkownicy*UserName*AppDataLocal.

2.  Rozwiń każdego pliku VSIX do folderu w tej samej lokalizacji:

    1.  Zmień rozszerzenie nazwy pliku z **.vsix** do **.zip**.

    2.  Wyodrębnij zawartość pliku zip do folderu.

    3.  Usuń plik zip

3.  Uruchom ponownie [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)].
