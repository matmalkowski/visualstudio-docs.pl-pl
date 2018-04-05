---
title: Visual Studio i Xamarin | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/30/2018
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-ide-mobile
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1da4064f-af69-472c-8f31-98484be5f790
caps.latest.revision: 10
author: charlespetzold
ms.author: chape
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: be1739a83e05ca55fa288fa707b37fddb095cc57
ms.sourcegitcommit: a0a49cceb0fdc1465ddf76d131c6575018b628b8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2018
---
# <a name="visual-studio-and-xamarin"></a>Visual Studio i Xamarin

Xamarin jest to platforma programistyczna aplikacji mobilnej do tworzenia natywnych iOS, Android i Windows aplikacji ze wspólnego C# / .NET kod base. Aplikacje napisane na platformie Xamarin można osiągnąć 75% do prawie 100% kodu ponownego użycia między platformami. Te aplikacje mają pełny dostęp do podstawowej platformy interfejsów API i dołączyć do nich interfejsy macierzystego użytkownika. One kompilacji do specyficznego dla platformy pakietów z mały wpływ na wydajność środowiska uruchomieniowego. (Uwaga: program Xamarin obsługuje również F #, ale w tej dokumentacji koncentruje się na C# tylko. Visual Basic nie jest obsługiwana w tej chwili.)  
  
Znajomość języka C# .NET i Visual Studio deweloperzy mogą używać tej samej mocy i wydajności, podczas pracy z platformą Xamarin dla aplikacji mobilnych. Te korzyści obejmują zdalnego debugowania na urządzeniach z systemem Android, iOS i Windows, bez konieczności uczenia się natywnego kodowania w językach Objective-C lub Java. Jest mało niespodziewanego, a następnie tak wielu aplikacji wysokiej wydajności za pomocą interfejsów użytkownika doskonałych — takie jak NASCAR, Aviva i MixRadio — zostały utworzone za pomocą platformy Xamarin.  
  
Ta dokumentacja pomoże Ci ocenić pełną moc **programu Visual Studio z platformą Xamarin** do tworzenia tych środowisk.  
  
-   Rozpoczynać [Instalatora i zainstaluj](../cross-platform/setup-and-install.md), proces, który może potrwać jakiś czas (zwykle 2-4 godzin w zależności od prędkości połączenia internetowego, co została już zainstalowana, a wybrane opcje).  
  
-   Gdy pliki instalacyjne są uruchomione, można [Dowiedz się więcej o programowanie przenośnych za pomocą platformy Xamarin](learn-about-mobile-development-with-xamarin.md) który informuje o rodzaju Xamarin, porównaj platformy Xamarin.Forms do natywnego interfejsu użytkownika i inne.  
  
-   Po zakończeniu instalacji [Sprawdź środowisku Xamarin](../cross-platform/verify-your-xamarin-environment.md).  
  
-   Zakończ za pośrednictwem samouczka [Dowiedz się podstawowe informacje dotyczące tworzenia aplikacji z platformy Xamarin.Forms w programie Visual Studio](/learn-app-building-basics-with-xamarin-forms-in-visual-studio.md).  
  
Można pracować z wszystkimi funkcjami Xamarin przy użyciu [dowolnej wersji programu Visual Studio 2017](https://www.visualstudio.com/vs) (Community, Professional i Enterprise). Nie jest wymagana żadna licencja oddzielne.  
  
> [!NOTE]
>  Te instrukcje opisują konfiguracji komputera najprostszy i najbardziej oczywistym dla deweloperów, którzy mają tła systemu Windows i programu Visual Studio. W tej konfiguracji ogólnej środowisko programistyczne jest uproszczone, ponieważ należy do interakcji z Mac, aby użyć symulatora systemu iOS i powiązane urządzenia. Jeśli zamiast tego pochodzą z tła Mac, zaleca się działanie programu Visual Studio wewnątrz równoleżników lub VMWare, albo za pomocą programu Visual Studio dla komputerów Mac. Zapoznaj się [Instalatora, instalacja i weryfikacja dla użytkowników komputerów Mac](../cross-platform/setup-install-and-verifications-for-mac-users.md) instrukcje.  
  
> [!NOTE]
>  Jeśli szukasz rozwiązania aplikacji dla wielu platform w formacie HTML i CSS, zapoznaj się programu Visual Studio Tools for Apache Cordova zgodnie z opisem w [aplikacji dla wielu Platform w programie Visual Studio](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#HTML).