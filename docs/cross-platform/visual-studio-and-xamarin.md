---
title: Visual Studio i Xamarin | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1da4064f-af69-472c-8f31-98484be5f790
caps.latest.revision: "10"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: xamarin
ms.openlocfilehash: 272b648b7b7bc27ae2f043a3a3d0541c87822258
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="visual-studio-and-xamarin"></a>Visual Studio i Xamarin
Xamarin jest to platforma programistyczna aplikacji mobilnej do tworzenia natywnych iOS, Android i Windows aplikacji ze wspólnego C# / .NET kod elementu bazowego, uzyskanie 75% do prawie 100% kodu ponownego użycia między platformami. Aplikacje napisane na platformie Xamarin i C# ma pełny dostęp do podstawowej platformy interfejsów API i interfejsów użytkownika natywnej kompilacji i skompilować specyficzne dla platformy pakietów, tak aby mały wpływ na wydajność środowiska uruchomieniowego. (Uwaga: program Xamarin obsługuje również F #, ale w tej dokumentacji koncentruje się na C# tylko. Visual Basic nie jest obsługiwana w tej chwili.)  
  
 Nadal, lepiej deweloperzy zapoznać się z C# .NET i Visual Studio będzie korzysta z takich samych możliwości i wydajność podczas pracy z platformą Xamarin dla aplikacji mobilnych, w tym zdalnego debugowania na urządzeniach z systemem Android, iOS i Windows — bez konieczności uczenia się kodu natywnego języków, takich jak Objective-C lub Java. Jest mało niespodziewanego, a następnie tak wielu aplikacji wysokiej wydajności za pomocą interfejsów użytkownika doskonałych — takie jak NASCAR, Aviva i MixRadio — zostały utworzone za pomocą platformy Xamarin.  
  
 Ta dokumentacja pomoże Ci ocenić pełnego zestawu funkcji **programu Visual Studio z platformą Xamarin** do tworzenia tych środowisk.  
  
-   Rozpoczynać [Instalatora i zainstaluj](../cross-platform/setup-and-install.md), proces, który może potrwać jakiś czas (zwykle 2-4 godzin w zależności od prędkości połączenia internetowego, co została już zainstalowana, a wybrane opcje).  
  
-   Gdy pliki instalacyjne są uruchomione, można [Dowiedz się więcej o programowanie przenośnych za pomocą platformy Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md) który informuje o rodzaju Xamarin, porównaj platformy Xamarin.Forms do natywnego interfejsu użytkownika i inne.  
  
-   Po zakończeniu instalacji [Sprawdź środowisku Xamarin](../cross-platform/verify-your-xamarin-environment.md).  
  
-   Zakończ za pośrednictwem samouczka [Dowiedz się podstawowe informacje dotyczące tworzenia aplikacji z platformy Xamarin.Forms w programie Visual Studio](../cross-platform/learn-app-building-basics-with-xamarin-forms-in-visual-studio.md).  
  
 Można pracować z wszystkimi funkcjami Xamarin za pośrednictwem [dowolnej wersji programu Visual Studio 2015](https://www.visualstudio.com/vs-2015-product-editions) (Community, Professional i Enterprise). Należy też zauważyć, że począwszy od 31 marca 2016, Xamarin jest dostępna we wszystkich wersjach programu Visual Studio 2015 i nie wymaga już oddzielnej licencji. W przypadku programu Visual Studio 2013, możesz zainstalować Xamarin oddzielnie, jako [Instalatora i zainstaluj](../cross-platform/setup-and-install.md) temacie.  
  
> [!NOTE]
>  Te instrukcje opisano konfigurację komputera najprostszy i najbardziej oczywistym te, które mają tła systemu Windows i programu Visual Studio. W tej konfiguracji ogólnej środowisko programistyczne jest uproszczone, ponieważ należy do interakcji z komputerów Mac, aby użyć symulatora systemu iOS i urządzenia powiązanego. Jeśli zamiast tego pochodzą z tła Mac, zaleca się działanie programu Visual Studio wewnątrz równoleżników/VMWare albo za pomocą platformy Xamarin Studio Community. Zapoznaj się [Instalatora, instalacja i weryfikacja dla użytkowników komputerów Mac](../cross-platform/setup-install-and-verifications-for-mac-users.md) instrukcje.  
  
> [!NOTE]
>  Jeśli szukasz rozwiązania aplikacji dla wielu platform w formacie HTML i CSS, zapoznaj się programu Visual Studio Tools for Apache Cordova zgodnie z opisem w [aplikacji dla wielu Platform w programie Visual Studio](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#HTML).