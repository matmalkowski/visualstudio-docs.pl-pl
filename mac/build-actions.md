---
title: Tworzenie działania
description: W tym artykule opisano różne akcje kompilacji, które mogą być używane dla projektów C#
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.assetid: 5399BCB1-E317-4C7B-87B1-C531E985DE6E
ms.openlocfilehash: 889414d391a4a894879399317d782df58a8bacb3
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33865009"
---
# <a name="build-actions"></a>Tworzenie działania

Wszystkie pliki w programie Visual Studio dla projektu Mac mają Akcja kompilacji, która kontroluje, co się dzieje z pliku podczas kompilacji. Te opcje można ustawić przez kliknięcie prawym przyciskiem myszy dowolny plik i przechodząc do **Akcja kompilacji**, jak pokazano poniżej:

![Wybieranie Eksploratora rozwiązań fom akcji kompilacji kompilacji](media/projects-and-solutions-image1.png)

Akcje niektóre typowe kompilacji dla projektów C#:

* **Brak** — plik nie jest częścią kompilacji w żaden sposób — wystarczy znajduje się w projekcie, by mieć łatwy dostęp z IDE.
* **Kompiluj** — plik zostanie przekazany do kompilatora C# jako plik źródłowy.
* **EmbeddedResource** — plik zostanie przekazany do kompilatora C# jako zasób do osadzenia w zestawie. `System.Reflection` Przestrzeni nazw można odczytać pliku z zestawu.
* **Zawartości** — projekty dla platformy ASP.NET, te pliki będą dołączane jako część lokacji po jej wdrożeniu. Dla platformy Xamarin.iOS i Xamarin.Mac projektów będą one zawarte w pakiecie aplikacji.

Istnieje możliwość wybrać więcej niż jeden plik w Eksploratorze rozwiązań, dzięki czemu można ustawić akcji kompilacji do wielu plików jednocześnie.

Istnieją ponadto akcji kompilacji dla określonych projektów. Na przykład mieć projektów platformy Xamarin.iOS **BundleResource** kompilacji akcji, który zostanie dodany plik jako część pakietu aplikacji. Informacje o akcji określonej kompilacji platformy Xamarin.Android znajdują się w [proces kompilacji](/xamarin/android/deploy-test/building-apps/build-process#Build_Actions) przewodnik.