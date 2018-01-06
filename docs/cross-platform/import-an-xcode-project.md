---
title: Importowanie projektu XCode | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa4b8161-d98f-4a1a-9db3-520133bfc82f
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: xplat-cplusplus
ms.openlocfilehash: 9de84c4330bb87ad13b865bda39f9ecafab4debd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="import-an-xcode-project"></a>Importowanie projektu XCode
Microsoft Visual C++ for Cross Platform Mobile Development obsługuje przenoszenie projektów XCode do programu Visual Studio, w którym można tworzyć bibliotek i platform i udostępnianie kodu z innych projektów. Importuj z Kreatora XCode upraszcza proces importowania projektów i dzielenia kodu C++ w celów XCode dla użyj biblioteki statycznej lub kod projektu współużytkowanych. Możesz zarządzać kodem specyficzne dla systemu iOS w programie Visual Studio i nadal używać XCode scenorys i kompilacji. Informacje o tym, jak łatwo zmieniać kodu i z powrotem XCode i Visual Studio Zobacz Przenieś zmiany między XCode i Visual Studio.  
  
## <a name="using-the-import-from-xcode-wizard"></a>Przy użyciu Kreatora importu z XCode  
 W tym temacie przedstawiono sposób przenoszenia projektu XCode do programu Visual Studio, aby skorzystać z kodu do udostępniania i rozwiązań i platform. Jako warunek wstępny należy skojarzyć komputerów Mac dla programu Visual Studio, aby można było importowanie, eksportowanie i skompilowanie projektu. Aby uzyskać instrukcje dotyczące sposobu konfigurowania parowania, zobacz [Instalowanie i Konfigurowanie narzędzi do kompilacji przy użyciu systemu iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md). Należy również Udostępnij projekt XCode za pośrednictwem sieci lub przenieś go do komputera programu Visual Studio do importowania danych z Kreatora XCode.  
  
#### <a name="import-from-xcode"></a>Importuj z XCode  
  
1.  Na **pliku** menu, wybierz **nowy**, **importu**, **importu z XCode**. Spowoduje to uruchomienie **importu z XCode** Kreator okna dialogowego.  
  
     ![Wybierz docelowy projektu systemu XCode, aby zaimportować](../cross-platform/media/cppmdd_u2_importxcode_choose.PNG "CPPMDD_U2_ImportXCode_Choose")  
  
2.  W **wybierz projekt** okienku, wybierz przycisk Przeglądaj, aby wybrać plik .pbxproj XCode. Przejdź do pliku projektu w **pliku projektu XCode wybierz** okna dialogowego, a następnie wybierz pozycję **Otwórz**.  
  
     ![Wybierz plik projektu w oknie dialogowym pliku projektu Xcode wybierz](../cross-platform/media/cppmdd_u2_importxcode_browse.PNG "CPPMDD_U2_ImportXCode_Browse")  
  
     W Kreatorze importowania danych z XCode, wybierz opcję **dalej**.  
  
3.  W **docelowym obiektów docelowych** okienku wybierz elementy docelowe projektu XCode, można zaimportować do projektów programu Visual Studio. Obiekty docelowe XCode są podobne do projektów Visual Studio; Większość to kolekcja kodu i zasobów, które powodują powstanie pliku binarnego. XCode Kreatorze importowania danych z tylko umożliwia importowanie elementów docelowych, które powodują powstanie pliku binarnego, ale nie bibliotekę statyczną, jako docelowego miejsca docelowe. Obiekty docelowe biblioteki statycznej XCode podlegają następnego kroku.  
  
     ![Import z okienka docelowym obiektów docelowych kreatora XCode](../cross-platform/media/cppmdd_u2_importxcode_destination.jpg "CPPMDD_U2_ImportXCode_Destination")  
  
     Dla każdego obiektu docelowego wybrany w **elementy docelowe, aby zaimportować**, Kreator automatycznie wykrywa pliki kodu C++, które może zostać podzielony na projekt odrębnych bibliotek statycznych i umieszcza je **elementy projektu C++** sekcji. Inne kodu i zasoby są pozostawiane w **elementy projektu XCode** sekcji. Te staną się odrębnych bibliotek statycznych i projekty aplikacji w programie Visual Studio po ukończeniu pracy Kreatora importu. Domyślnie jednostki celów testowych i framework nie są dzielone na oddzielnych projektów przez kreatora.  
  
     Aby zmienić, które pliki są w każdym projekcie, górę i w dół. Po zakończeniu plików w każdym projekcie, wybierz **dalej** aby kontynuować.  
  
4.  W **cele biblioteki** okienku, wybierz, które biblioteki statycznej elementów docelowych w projekcie XCode, można zaimportować do projektów programu Visual Studio. W tym okienku są dostępne pliki, które są umieszczane w projekcie udostępnionym kodu i umieszczonych w projektach biblioteki statycznej. W każdym z elementów docelowych w **elementy docelowe, aby zaimportować** listy, możesz kontrolować, które pliki są umieszczane w **elementów projektu udostępnionego kodu** i **elementy projektu biblioteki statycznej** przy użyciu przyciski w górę i w dół.  
  
     ![Import z okienka cele biblioteki XCode](../cross-platform/media/cppmdd_u2_importxcode_library.jpg "CPPMDD_U2_ImportXCode_Library")  
  
     Projekt udostępniony kod jest sposób udostępniania zestaw między projektami w programie Visual Studio — pliki kodu źródłowego. Kod jest wbudowany w ramach projektu, który zawiera go, a nie jako własnego projektu. Ponieważ projektów, które obejmują udostępnionego kodu może mieć różne architektury i konfiguracji, to najlepszy sposób, aby zapewnić pojedynczego projektu, który zawiera kod, który może zostać utworzony dla wielu różnych platform.  
  
     Po zakończeniu plików w każdym projekcie, wybierz **dalej** aby kontynuować.  
  
5.  **Globalnych właściwości** okienku można ustawić ścieżkę wyszukiwania framework i ścieżkę wyszukiwania plików dołączanych nagłówka dla wszystkich projektów dla systemu iOS w programie Visual Studio. Visual Studio używa tych ścieżek, do przeglądania kodu źródłowego i IntelliSense. Tych ścieżek globalnych są przydatne podczas tworzenia projektów dla systemu iOS, które korzystanie ze wspólnego zestawu nagłówków i platform.  
  
     ![Importuj z okienka właściwości globalne XCode](../cross-platform/media/cppmdd_u2_importxcode_global.jpg "CPPMDD_U2_ImportXCode_Global")  
  
     Można również ustawić tych ścieżek globalnych w programie Visual Studio w **opcje** okna dialogowego. Można je znaleźć na **narzędzia** menu, wybierz opcję **opcje**. W **opcje** okna dialogowego, rozwiń węzeł **Cross Platform**, **C++**, **iOS**, **globalnych właściwości**.  
  
     Wybierz **dalej** aby kontynuować.  
  
6.  **Struktury** okienko jest używany do konfigurowania ścieżki używany przez Visual Studio do przeglądania i IntelliSense dla projektu. Ścieżki muszą być dostępne dla programu Visual Studio dla każdej platformy odwołuje się projekt XCode. Kreator sprawdza, czy ramach odwołania w projektów XCode i wskazuje, czy program Visual Studio można znaleźć platformę. Dowolną ścieżkę, które zostały już skonfigurowane we właściwościach globalne powinny zostać wykryte przez program Visual Studio. Wyjątki są wyświetlane na liście struktur. Dla każdej platformy x na liście należy podać ścieżkę dostępny komputera dla programu Visual Studio można znaleźć w ramach. Można użyć przycisku przeglądania [...] **wybierz Folder** okna dialogowego, aby znaleźć ścieżki. Ścieżka framework może być kopii lokalnej lub w udziale dostępne w sieci opartym na systemie  
  
     ![Importuj z okienka struktury XCode](../cross-platform/media/cppmdd_u2_importxcode_frameworks.jpg "CPPMDD_U2_ImportXCode_Frameworks")  
  
     Wybierz **dalej** aby kontynuować.  
  
7.  **Ustawienia projektu** okienko pozwala zmienić platformę i obejmują ustawienia ścieżki wyszukiwania nagłówka dla każdego projektu, Kreator tworzy. Użyj w tym okienku można ustawić ścieżki specyficznego dla projektu, które różnią się od ustawienia globalne.  
  
     Aby ustawić ścieżkę do określonego projektu w **projektu docelowego** listy rozwijanej, wybierz plik projektu, a następnie ustaw wartości **ścieżki wyszukiwania Framework** i **obejmują ścieżki wyszukiwania nagłówka** kontrolki. Można użyć przycisk Przeglądaj [...] obok każdego formantu **wybierz Folder** okna dialogowego, aby znaleźć ścieżki.  
  
     ![Importuj z okienka projektów XCode](../cross-platform/media/cppmdd_u2_importxcode_projects.jpg "CPPMDD_U2_ImportXCode_Projects")  
  
     Jeśli nie Mac zdalnego ma skojarzone z tym Komputerem w programie Visual Studio, konfiguracji, wyświetlany jest link maszyny zdalnej. Aby uzyskać instrukcje dotyczące sposobu konfigurowania parowania, zobacz [Instalowanie i Konfigurowanie narzędzi do kompilacji przy użyciu systemu iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md).  
  
     Aby zaimportować projekt XCode przy użyciu Kreatora ustawień, wybierz **zaimportować**.  
  
 Importuj z Kreatora XCode tworzy projekty w Visual Studio, która odpowiada wybrane elementy docelowe projektu XCode. Kod, który może być współużytkowana z innych projektów C++ jest podzielony na oddzielnych udostępniony kod i projekty biblioteki statycznej. Pozostały kod znajduje się w systemie iOS projektów biblioteki i aplikacji, które mogą być wbudowane zdalnie przez program Visual Studio. Aby uzyskać więcej informacji o przenoszeniu kod między XCode i Visual Studio, zobacz [zmiany synchronizacji między XCode i Visual Studio](../cross-platform/sync-changes-between-xcode-and-visual-studio.md).