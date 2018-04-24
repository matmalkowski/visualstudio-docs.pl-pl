---
title: Połączona usług w programie Visual Studio dla komputerów Mac
description: Dodawanie magazynu danych Azure, uwierzytelniania i powiadomień wypychanych do aplikacji mobilnych z poziomu programu Visual Studio dla komputerów Mac
ms.prod: xamarin
ms.assetid: 41CB62FF-0F39-4CE8-8917-6A77F058719F
author: asb3993
ms.author: amburns
ms.date: 04/04/2018
ms.openlocfilehash: 0e3cc587b2c29cab19a4a6cdeed0a4b138330726
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="connected-services-walkthrough"></a>Połączonych usług wskazówki

Przepływ pracy usług połączonych powoduje przeniesienie przepływu pracy portalu Azure do programu Visual Studio dla komputerów Mac, dzięki czemu nie trzeba pozostaw projekt, aby dodać usługi.

W tym przewodniku przedstawiono sposób dodawania usługi zaplecza Azure udostępnia magazyn danych w chmurze, uwierzytelnianie i wysyłanie powiadomień wypychanych do aplikacji platformy Xamarin.Forms przenośnej biblioteki klasy (PCL) i platform.


1.  Uruchomić przez dwukrotne kliknięcie **usług połączonych** węzła w rozwiązania, które zostaną wyświetlone **galerii usług**.
  To jest lista wszystkich dostępnych usług dla typu aplikacji. Wybierz usługę (takich jak **zaplecza aplikacji mobilnych w usłudze aplikacji Azure**), klikając go.

    [![Połączone węzła usług w programie Visual Studio for Mac](media/connected-services-image001-sml.png "węzła usług połączonych w programie Visual Studio dla komputerów Mac")](media/connected-services-image001.png#lightbox)

2. Na stronie Szczegóły usługi zawiera opis usługi i zależności do zainstalowania.
  Kliknij przycisk **Dodaj** przycisk, aby dodać zależności do aplikacji:

    [![Zaplecze aplikacji mobilnej z platformy Azure,](media/connected-services-image002-sml.png "zaplecze aplikacji mobilnej przy użyciu platformy Azure")](media/connected-services-image002.png#lightbox)

3. Zależności należy dodać do PCL i projekty specyficzne dla platformy do pracy.
  Zaznacz pola wyboru, aby dodać usługę do każdego projektu odwołującego się on (bezpośrednio lub pośrednio):

    [![Sprawdź wszystkie projekty, które powinny się odwoływać usługi](media/connected-services-image003-sml.png "Sprawdź wszystkie projekty, które powinien odwoływać się usługi")](media/connected-services-image003.png#lightbox)

4. Wybierz **Akceptuj** na **akceptacji licencji** okien dialogowych dla pakietów NuGet.
  Mogą być dwa okna dialogowe, aby zaakceptować, jeden dla MobileClient i zależności i drugi dla SQLiteStore, co jest niezbędne do synchronizacji danych w trybie offline:

    [![Zaakceptuj umowy licencyjne](media/connected-services-image004-sml.png "Zaakceptuj umowy licencyjne")](media/connected-services-image004.png#lightbox)

    ![Okno akceptacji licencji](media/connected-services-image005.png "okna akceptacji licencji")

5. Po dodaniu zależności, użytkownik zostanie zapytany do logowania się przy użyciu konta, którego chcesz używać do komunikowania się z platformą Azure.
  Jeśli użytkownik jest już zalogowany za pomocą Identyfikatora Microsoft, Visual Studio for Mac podejmie próbę pobrania subskrypcji platformy Azure i usług aplikacji skojarzonych z nimi. Jeśli nie masz żadnych subskrypcji, możesz dodać kategorię skorzystania z bezpłatnej wersji próbnej lub zakup planu subskrypcji w portalu Azure.

6. Wybierz usługę aplikacji z listy. To spowoduje wypełnienie kod szablonu `MobileServiceClient` obiektu z odpowiedni adres URL usługi app Service na platformie Azure:

    [![Wybierz z listy aplikacji usługi](media/connected-services-image006-sml.png "wybierz usługę aplikacji z listy")](media/connected-services-image006.png#lightbox)

    Jeśli nie ma na liście usług, kliknij przycisk **nowy** przycisk (zobacz krok 9).

7. Skopiuj kod szablonu `MobileServiceClient` do PCL. Lokalizacja pliku nie jest ważna, tak długo, jak istnieje tylko jedno wystąpienie.
  Zalecanym podejściem jest utworzenie `AzureService` klasy, która obsługuje wszystkie interakcje Azure i używa `MobileServiceClient`:

    ![Skopiuj kod konfiguracji do region](media/connected-services-image007.png "skopiuj kod konfiguracji do aplikacji")

8. Postępuj zgodnie z dokumentacją w **następne kroki** dodawania danych, synchronizacja w trybie offline, uwierzytelniania i powiadomienia wypychane do aplikacji:

    [![Przejrzyj następnej instrukcji kroki](media/connected-services-image008-sml.png "przejrzeć instrukcje dla następnej czynności")](media/connected-services-image008.png#lightbox)

9. Jeśli nie masz żadnych istniejących usług aplikacji, można utworzyć nowych usług z poziomu programu Visual Studio dla komputerów Mac.
  Kliknij przycisk **nowy** przycisk w lewym dolnym rogu listy usług, aby otworzyć **nowej aplikacji usługi** okna dialogowego:

    [![Utwórz nową usługę aplikacji w programie Visual Studio for Mac](media/connected-services-image009-sml.png "Utwórz nową usługę aplikacji w programie Visual Studio dla komputerów Mac")](media/connected-services-image009.png#lightbox)

Nowa usługa wymaga następujących parametrów:

-   **Nazwa aplikacji usługi** — Unikatowy identyfikator/nazwę planu
-   **Subskrypcja** — subskrypcji chcesz płacisz za usługę
-   **Grupa zasobów** — lub sposób organizowania wszystkich zasobów platformy Azure dla projektu. Opcja Użyj istniejących lub Utwórz nową. Jeśli jest to pierwszy usługi Azure, Utwórz nową.
-   **Planowanie usługi** — Określa lokalizację i koszt wszystkich zasobów, które go używają. Opcja Użyj istniejących lub Utwórz nową. Jeśli jest to pierwszy usługi Azure, użyj ustawienia domyślnego lub Utwórz nową w warstwie bezpłatna (F1).

Odwiedź stronę [dokumentacji usługi Azure App Service](https://azure.microsoft.com/documentation/learning-paths/appservice-mobileapps/) Aby uzyskać więcej informacji.
