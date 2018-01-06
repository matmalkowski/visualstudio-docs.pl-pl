---
title: "Synchronizowanie zmian między XCode i Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c71a4d7c-120e-4559-a114-3a99c4b860a9
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: xamarin
ms.openlocfilehash: 6913ffc5f2a0515b2682036b46ec8c164e9f877b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="sync-changes-between-xcode-and-visual-studio"></a>Synchronizacja zmian między XCode i Visual Studio
Microsoft Visual C++ dla składnika aplikacji mobilnych zawiera funkcje zdalnego do synchronizowania pracy między danym Komputerem a z komputerów Mac. Podczas parowania są komputery Mac i Visual Studio, nowe opcje są dostępne dla systemu iOS projektów aplikacji w programie Visual Studio, który umożliwia Otwórz projekt w programie XCode, Przenieś swój kod między XCode i Visual Studio i czyszczenie katalogu tymczasowego projektu XCode.  
  
 Aby użyć opcji komputer zdalny, projektu musi być projekt aplikacji systemu iOS oraz programu Visual Studio musi łączyć się z Twojego Mac. Wymagania wstępne i instrukcje dotyczące sposobu pary Mac, zobacz [Instalowanie i Konfigurowanie narzędzi do kompilacji przy użyciu systemu iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md).  
  
## <a name="the-remote-machine-menu"></a>Menu maszyny zdalnej  
 W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt aplikacji systemu iOS, aby wyświetlić menu kontekstowe. Wybierz **maszyny zdalnej** element, aby wyświetlić dostępne opcje zdalnego.  
  
 ![Komputer zdalny element menu w Eksploratorze rozwiązań](../cross-platform/media/cppmdd_u2_remotemachine_menu.jpg "CPPMDD_U2_RemoteMachine_Menu")  
  
 Te polecenia pozwalają Otwórz projekt w programie XCode, przenoszeniu lokalne zmiany lub całego projektu programu Visual Studio i XCode i oczyścić plików tymczasowych na komputerze zdalnym.  
  
### <a name="open-in-xcode"></a>Otwórz w programie XCode  
 Aby otworzyć projekt w programie XCode z programu Visual Studio na **maszyny zdalnej** podmenu, wybierz **Otwórz w programie XCode** można otworzyć wybranego projektu na komputerze zdalnym sparowany. Serwer vcremote jest używany do otwierania XCode na komputerze Mac i przejdź do katalogu tymczasowego utworzona na komputerze Mac, który zawiera kopię projektu. Visual Studio powoduje wyświetlenie okna dialogowego, które zawiera katalog tymczasowy używany dla projektu. Akcje wykonywane na komputerze zdalnym są także wyświetlane w **dane wyjściowe** okna w programie Visual Studio. Aby je wyświetlić, konieczne może być wybierz **Visual C++ maszyny zdalnej** w **Pokaż dane wyjściowe z** listy rozwijanej w górnej części **dane wyjściowe** okna.  
  
 ![W oknie danych wyjściowych zawiera akcje maszyny zdalnej. ] (../cross-platform/media/cppmdd_u2_remotemachine_output.png "CPPMDD_U2_RemoteMachine_Output")  
  
 Na komputerze Mac można użyć narzędzia XCode do edycji kodu i zasobów, scenorys i akcji. W programie Visual Studio projekt aplikacji systemu iOS jest oznaczony za pomocą "Otworzyć w programie XCode" Aby wskazać, że mogą być dokonywane zmiany na maszynie zdalnej. Po zakończeniu edycji ściągania od zdalnego lub przyrostowych ściąganie danych z poleceń zdalnych można użyć do skopiowania zmiany do projektu programu Visual Studio.  
  
### <a name="push-to-remote-and-incremental-push-to-remote"></a>Wypychanie do zdalnego i przyrostowych powiadomień wypychanych do zdalnego  
 Jeśli wprowadzono zmiany do projektu aplikacji systemu iOS w programie Visual Studio, powiadomień wypychanych do zdalnego i przyrostowych wypychanie poleceń zdalnych może służyć do przenoszenia plików projektu zmienione sparowanego komputer zdalny. Naciśnij, aby polecenia zdalnego kopiuje wszystkie pliki projektu na komputerze zdalnym. Tylko przyrostowe wypychania do polecenia zdalnego kopiuje zmienione pliki z komputerem zdalnym. W przypadku dużych projektów z niewielkich zmian przyrostowe polecenia można zaoszczędzić czas i przepustowości.  
  
 Aby skopiować pliki projektu na komputerze Mac, w programie Visual Studio w **Eksploratora rozwiązań** okna, kliknij prawym przyciskiem myszy projekt aplikacji systemu iOS, aby otworzyć menu kontekstowe. Wybierz **maszyny zdalnej** i wybrać opcję **wypychania do zdalnego** lub **przyrostowe wypychania do zdalnego** do kopiowania plików projektu w programie Visual Studio na komputerze Macintosh.  
  
### <a name="pull-from-remote-and-incremental-pull-from-remote"></a>Ściąganie danych z zdalnego i przyrostowych ściągania od zdalnego  
 Po wprowadzeniu zmian do projektu w programie XCode, przenieść zmiany z powrotem do programu Visual Studio do synchronizowania projektów.  
  
 Aby skopiować pliki projektu z komputerów Mac, w programie Visual Studio w **Eksploratora rozwiązań** okna, kliknij prawym przyciskiem myszy projekt aplikacji systemu iOS, aby otworzyć menu kontekstowe. Wybierz **maszyny zdalnej** i wybrać opcję **ściąganie danych z zdalnego** lub **przyrostowe ściąganie danych z zdalnego** do kopiowania plików projektu z komputerów Mac dla programu Visual Studio.  
  
### <a name="clean-remote"></a>Zdalne czyszczenie  
 Polecenia czystą zdalnego służy do usuwania plików w katalogu tymczasowego projektu na komputerze zdalnym. Zawartość katalogu, takich jak pliki źródłowe produktów kompilacji są usuwane opartym na systemie Upewnij się, że wszelkie zmiany, które chcesz zachować wstecz do programu Visual Studio za pomocą ściągnięcia ze zdalnej lub przyrostowych ściągnięcia ze zdalnej, przed użyciem polecenia czystą zdalnego zostały zsynchronizowane.  
  
 Aby wyczyścić katalogu tymczasowego projektu na komputerze zdalnym, w programie Visual Studio w **Eksploratora rozwiązań** okna, kliknij prawym przyciskiem myszy projekt aplikacji systemu iOS, aby otworzyć menu kontekstowe. Wybierz **maszyny zdalnej** i wybierz polecenie **czystą zdalnego** Aby usunąć pliki katalogu projektu z Twojej Mac.