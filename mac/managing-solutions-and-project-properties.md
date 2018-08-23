---
title: Zarządzanie właściwościami projektów i rozwiązań
description: W tym artykule opisano, jak Zarządzanie właściwościami projektów i rozwiązań w programie Visual Studio dla komputerów Mac
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 75247EB8-323A-4AFD-A451-6703A03D5D1F
ms.openlocfilehash: dbfff9dcb03958ce2a8aa6bd2d2940ee79908dee
ms.sourcegitcommit: 2597236a481afbaf1ad4915743898ee1aee49760
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/10/2018
ms.locfileid: "42624013"
---
# <a name="managing-project-and-solution-properties"></a>Zarządzanie właściwościami projektów i rozwiązań

## <a name="project-options"></a>Opcje projektu

Opcje projektu są specyficzne dla każdego projektu i wpływają na sposób uruchamiania, wbudowane i zapisywane projektu. To zachowanie różni się od programu Visual Studio Preferencje systemu Mac (która ustawia opcje użytkownika) i opcje rozwiązań, (które ustawić opcje dla całego rozwiązania). Opcje projektu są przechowywane w pliku projektu (.csproj), tak, aby skompilować i uruchomić projekt poprawnie innym deweloperom. Posiadanie opcje określonego projektu umożliwia wielu deweloperów pracowało nad tym samym dokumencie bez uszczerbku dla formatu pliku.

Aby otworzyć projekt opcje w programie Visual Studio dla komputerów Mac kliknij dwukrotnie nazwę projektu, lub kliknij prawym przyciskiem myszy, aby otworzyć menu kontekstowe i wybierz **opcje**:

 ![Opcja menu kontekstowego](media/projects-and-solutions-image2.png)

Można edytować opcje obejmują funkcje umożliwiające tworzenie, uruchamianie i kod źródłowy zestawu i opcje kontroli wersji.

Opcje projektu są zorganizowane w pięciu różnych kategoriach:

* **Ogólne** -projekt informacje, takie jak nazwa, opis i domyślne Namespace są ustawione w tym miejscu wraz z lokalizacją projektu.
* **Tworzenie** — dzięki temu deweloperzy mogą ustawić lub zmienić PCL profilów dla biblioteki klas przenośnych. Umożliwia ona również poleceń niestandardowych, konfiguracji, można ustawić opcje kompilatora. Można również tutaj ustawić dane wyjściowe ścieżka i nazwa zestawu.
* **Uruchom** — dzięki temu można tworzyć niestandardowe konfiguracje wykonywania na poszczególnych projektów.
* **Kod źródłowy** — to pozwala na kontrolowanie formatowania wiele różnych typów plików i konwencje nazewnictwa. Można również ustawić zasady nazewnictwa i style nagłówków domyślne w tym miejscu w całym dokumencie.
* **Kontrola wersji** — dzięki temu można edytować styl komunikatu dotyczącego zatwierdzenia w ramach kontroli wersji z projektem.

Każdy projekt może zawierać opcje określonego projektu, w zależności od platformy. Na przykład projekt Xamarin.Android tak jak pokazano na poniższej ilustracji, zawiera opcje związane z kompilacja systemu Android — takich jak opcje konsolidatora; i aplikacji — na przykład uprawnienia:

 ![Opcje projektu dla systemu android](media/projects-and-solutions-image5.png)

Xamarin.iOS zawiera opcje związane z do podpisania pakietu — takie jak wymagany profil inicjowania obsługi administracyjnej do użycia:

 ![Opcje projektu systemu iOS](media/projects-and-solutions-image6.png)

## <a name="solution-options"></a>Opcje rozwiązania 

Opcje rozwiązania są podobne do opcji projektu, ale obejmują zakres całego rozwiązania. Zapewniają one sposób, aby ustawić informacje o autorze, ustawienia i formatowanie style i kontroli wersji kodu kompilacji i umożliwiają one sposób przypisania projektem startowym w rozwiązaniu.  W oknie dialogowym Opcje rozwiązania są dostępne z **Projekt > Opcje rozwiązania** elementu menu z **opcje** rozwiązania, w konsoli rozwiązania lub przez dwukrotne kliknięcie w menu kontekstowym Rozwiązanie w konsoli rozwiązania:

 ![Opcje rozwiązania](media/projects-and-solutions-image7.png)
