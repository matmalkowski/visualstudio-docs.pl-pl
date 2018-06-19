---
title: Zarządzanie właściwościami projektów i rozwiązań
description: W tym artykule opisano, jak zarządzać właściwościami projektów i rozwiązań w programie Visual Studio dla komputerów Mac
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.assetid: 75247EB8-323A-4AFD-A451-6703A03D5D1F
ms.openlocfilehash: 7eec0bdecd09a0776df4ab0a9cb21ea37fbabf0b
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33866042"
---
# <a name="managing-project-and-solution-properties"></a>Zarządzanie właściwościami projektów i rozwiązań

## <a name="project-options"></a>Opcje projektu

Opcje projektu są specyficzne dla każdego projektu i wpłynąć na sposób Uruchom, utworzony i zapisany projektu. To zachowanie różni się od programu Visual Studio Preferencje systemu Mac (który określa opcje użytkownika) i rozwiązania (które skonfigurować opcje dla całego rozwiązania). Opcje projektu są przechowywane w pliku projektu (.csproj), aby skompilować i uruchomić projekt poprawnie innymi deweloperami. Po opcji określonego projektu umożliwia wielu deweloperom pracować na tym samym dokumencie bez naruszania format pliku.

Aby otworzyć projekt opcji w programie Visual Studio for Mac kliknij dwukrotnie nazwę projektu, lub kliknij prawym przyciskiem myszy, aby otworzyć menu kontekstowe i wybierz **opcje**:

 ![Opcja menu kontekstowego](media/projects-and-solutions-image2.png)

Można edytować opcje obejmują opcje do tworzenia, uruchamiania i Ustaw kod źródłowy i kontroli wersji.

Opcje projektu są zorganizowane w pięciu różnych kategorii:

* **Ogólne** -projektu informacje, takie jak nazwa, opis i Namespace domyślne są ustawione w tym miejscu wraz z lokalizacji projektu.
* **Tworzenie** — dzięki temu deweloperzy mogą ustawić lub zmienić PCL profilów dla przenośnej biblioteki klas. Umożliwia także polecenia niestandardowych, konfiguracji, opcji kompilatora. Nazwa ścieżki i zestawu wyjściowego można ustawić także w tym miejscu.
* **Uruchom** — dzięki temu można utworzyć niestandardowe konfiguracje wykonywania na podstawie na projekt.
* **Kod źródłowy** — to pozwala na kontrolowanie formatowanie wielu różnych typów plików i konwencje nazewnictwa. Można również ustawić zasady nazewnictwa i domyślne style nagłówka w tym miejscu w całym dokumencie.
* **Kontrola wersji** — dzięki temu można edytować styl komunikatu zatwierdzania podczas korzystania z kontroli wersji z projektu.

Każdy projekt może zawierać opcji określonego projektu, w zależności od platformy. Na przykład projekt platformy Xamarin.Android, tak jak pokazano na poniższej ilustracji, ma opcje związane z Android kompilacji — takich jak opcje konsolidatora; a aplikacja — takie jak uprawnienia:

 ![Opcje projektu systemu android](media/projects-and-solutions-image5.png)

Xamarin.iOS ma opcje związane z podpisywania pakietu — takie jak wymagany profil inicjowania obsługi administracyjnej:

 ![Opcje projektu systemu iOS](media/projects-and-solutions-image6.png)

## <a name="solution-options"></a>Opcje rozwiązania 

Opcje rozwiązania są podobne opcje projektu, ale obejmuje zakres całego rozwiązania. Stanowią sposób, aby ustawić informacje o autorze, ustawienia i formatowania, style i kontroli wersji kodu kompilacji i pozwalają one na sposób przypisywania projekt startowy w rozwiązaniu.  Okno dialogowe Opcje rozwiązania są dostępne z **projektu > Opcje rozwiązania** element menu z **opcje** elementu menu kontekstowego w ramach rozwiązania w konsoli rozwiązania lub przez dwukrotne kliknięcie Rozwiązanie w konsoli rozwiązania:

 ![Opcje rozwiązania](media/projects-and-solutions-image7.png)
