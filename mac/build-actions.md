---
title: "Tworzenie działania"
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 5399BCB1-E317-4C7B-87B1-C531E985DE6E
ms.openlocfilehash: 78b0e715ca44c613b6a7ee839c0656e301308588
ms.sourcegitcommit: ebe9fb5eda724936f7a059d35d987c29dffdb50d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2017
---
# <a name="build-actions"></a>Tworzenie działania 

Wszystkie pliki w programie Visual Studio dla projektu Mac mają Akcja kompilacji, która kontroluje, co się dzieje z pliku podczas kompilacji. Te opcje można ustawić przez kliknięcie prawym przyciskiem myszy dowolny plik i przechodząc do **Akcja kompilacji**, jak pokazano poniżej:

![](media/projects-and-solutions-image1.png)

Akcje niektóre typowe kompilacji dla projektów C#:

* **Brak** — plik nie jest częścią kompilacji w żaden sposób — wystarczy znajduje się w projekcie, by mieć łatwy dostęp z IDE.
* **Kompiluj** — plik zostanie przekazany do kompilatora C# jako plik źródłowy.
* **EmbeddedResource** — plik zostanie przekazany do kompilatora C# jako zasób do osadzenia w zestawie. `System.Reflection` Przestrzeni nazw można odczytać pliku z zestawu.
* **Zawartości** — projekty dla platformy ASP.NET, te pliki będą dołączane jako część lokacji po jej wdrożeniu. Dla platformy Xamarin.iOS i Xamarin.Mac projektów będą one zawarte w pakiecie aplikacji.

Istnieje możliwość wybrać więcej niż jeden plik w Eksploratorze rozwiązań, dzięki czemu można ustawić akcji kompilacji do wielu plików jednocześnie.

Istnieją ponadto akcji kompilacji dla określonych projektów. Na przykład mieć projektów platformy Xamarin.iOS **BundleResource** kompilacji akcji, który zostanie dodany plik jako część pakietu aplikacji. Informacje o akcji określonej kompilacji platformy Xamarin.Android znajdują się w [proces kompilacji](https://developer.xamarin.com/guides/android/under_the_hood/build_process/#Build_Actions) Przewodnik po developer.xamarin.com.