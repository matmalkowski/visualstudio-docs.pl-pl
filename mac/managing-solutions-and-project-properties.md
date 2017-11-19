---
title: "Zarządzanie właściwościami projektów i rozwiązań | Dokumentacja firmy Microsoft"
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 75247EB8-323A-4AFD-A451-6703A03D5D1F
ms.openlocfilehash: 8871ab002a94a9c0bbc0063a25b4dea9cb271142
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="managing-project-and-solution-properties"></a>Zarządzanie właściwościami projektów i rozwiązań

## <a name="project-options"></a>Opcje projektu

Opcje projektu są specyficzne dla każdego projektu i wpłynąć na sposób Uruchom, utworzony i zapisany projektu. To zachowanie różni się od programu Visual Studio for Mac preferencje ustawić opcje specyficzne dla użytkownika, oraz opcje rozwiązania, które opcje dla całego rozwiązania. Opcje projektu są przechowywane w pliku projektu (.csproj), aby skompilować i uruchomić projekt poprawnie innymi deweloperami. Dzięki temu wiele deweloperzy mogą działać na tym samym dokumencie bez naruszania format pliku.

Projekt opcje programu Visual Studio dla komputerów Mac można uruchomić przez dwukrotne kliknięcie nazwy projektu lub przez kliknięcie prawym przyciskiem myszy, aby otworzyć menu kontekstowe i wybierając **opcje**:

 ![Opcja menu kontekstowego](media/projects-and-solutions-image2.png)

Można edytować opcje dołączyć do tworzenia, uruchamiania i ustaw opcje kontroli źródła kod i wersja.

Opcje projektu są zorganizowane w pięciu różnych kategorii, które mają następujące możliwości:

* **Ogólne** -projektu informacje takie jak nazwa, opis i Namespace domyślne można ustawić w tym miejscu, wraz z lokalizacji projektu.
* **Tworzenie** — dzięki temu deweloperzy mogą ustawić lub zmienić PCL profilów dla przenośnej biblioteki klas. Umożliwia także polecenia niestandardowych, konfiguracji, opcji kompilatora. Nazwa ścieżki i zestawu wyjściowego można ustawić także w tym miejscu.
* **Uruchom** — dzięki temu można utworzyć niestandardowe konfiguracje wykonywania na podstawie na projekt.
* **Kod źródłowy** — to pozwala na kontrolowanie formatowanie wielu różnych typów plików i konwencje nazewnictwa. Można również ustawić zasady nazewnictwa i domyślne style nagłówka w tym miejscu w całym dokumencie.
* **Kontrola wersji** — dzięki temu można edytować styl komunikatu zatwierdzania podczas korzystania z kontroli wersji z projektu.

Każdy projekt może również zawierać opcje określonego projektu, w zależności od platformy. Na przykład projekt platformy Xamarin.Android, jak pokazano poniżej, ma opcje związane z Android kompilacji — takich jak opcje konsolidatora; a aplikacja — takie jak uprawnienia:

 ![Opcje projektu systemu android](media/projects-and-solutions-image5.png)

Xamarin.iOS będzie zawierać opcje związane z podpisywania pakietu — takie jak wymagany profil inicjowania obsługi administracyjnej; i odnoszących się do IPA opcje tworzenia pakietów:

 ![Opcje projektu systemu iOS](media/projects-and-solutions-image6.png)

## <a name="solution-options"></a>Opcje rozwiązania 

Opcje rozwiązania są podobne opcje projektu, ale obejmuje zakres całego rozwiązania. Stanowią sposób, aby ustawić informacje o autorze, ustawienia i formatowania, style i kontroli wersji kodu kompilacji i pozwalają one na sposób przypisywania projekt startowy w rozwiązaniu.  Okno dialogowe Opcje rozwiązania są dostępne z **projektu > Opcje rozwiązania** element menu z **opcje** elementu menu kontekstowego w ramach rozwiązania w konsoli rozwiązania lub przez dwukrotne kliknięcie Rozwiązanie w konsoli rozwiązania:

 ![Opcje rozwiązania](media/projects-and-solutions-image7.png)
