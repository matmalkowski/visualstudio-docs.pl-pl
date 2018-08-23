---
title: Akcja kompilacji
description: W tym artykule opisano różne akcje kompilacji, których można użyć dla projektów C#
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 5399BCB1-E317-4C7B-87B1-C531E985DE6E
ms.openlocfilehash: 6ef2cc3347480fceab23df12e53be65dd5432183
ms.sourcegitcommit: 2597236a481afbaf1ad4915743898ee1aee49760
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/10/2018
ms.locfileid: "42623937"
---
# <a name="build-actions"></a>Akcja kompilacji

Wszystkie pliki w programie Visual Studio dla komputerów Mac projektu mają akcji kompilacji, który kontroluje, co się dzieje z pliku podczas kompilacji. Te opcje można ustawić przez kliknięcie prawym przyciskiem myszy dowolny plik i przechodząc do **Build Action**, jak pokazano poniżej:

![Wybieranie Eksploratora rozwiązań produkcyjny akcji kompilacji kompilacji](media/projects-and-solutions-image1.png)

Akcje niektóre typowe kompilacji dla projektów języka C#:

* **Brak** — plik nie jest częścią kompilacji w jakikolwiek sposób — po prostu znajduje się w projekcie, aby mieć łatwy dostęp z poziomu środowiska IDE.
* **Skompilować** — plik zostanie przekazany do kompilatora C# jako plik źródłowy.
* **EmbeddedResource** — plik zostanie przekazany do kompilatora C# jako zasób do osadzenia w zestawie. `System.Reflection` Przestrzeni nazw można odczytać pliku z zestawu.
* **Zawartość** — dla projektów platformy ASP.NET, te pliki będą dołączane jako część lokacji podczas jej wdrażania. W przypadku projektów Xamarin.iOS i Xamarin.Mac będzie znajdować się w zbiorze aplikacji.

Użytkownik może wybrać więcej niż jeden plik w Eksploratorze rozwiązań, co pozwala ustawić akcji kompilacji do wielu plików jednocześnie.

Ponadto istnieją akcje kompilacji dla konkretnych projektów. Na przykład mieć projekty Xamarin.iOS **BundleResource** tworzenie akcji, która doda go jako część pakietu aplikacji. Informacje o akcjach określonej kompilacji platformy Xamarin.Android znajdują się w [proces kompilacji](/xamarin/android/deploy-test/building-apps/build-process#Build_Actions) przewodnik.