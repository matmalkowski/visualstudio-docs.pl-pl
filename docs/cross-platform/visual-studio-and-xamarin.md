---
title: Visual Studio i Xamarin | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/30/2018
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 1da4064f-af69-472c-8f31-98484be5f790
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: caf1ea462cc69366f11e4768003707e9cc263327
ms.sourcegitcommit: 9765b3fcf89375ca499afd9fc42cf4645b66a8a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/20/2018
ms.locfileid: "46495742"
---
# <a name="visual-studio-and-xamarin"></a>Visual Studio i Xamarin

Xamarin to platforma do tworzenia aplikacji mobilnych, do tworzenia natywnych dla systemów iOS, Android i Windows aplikacje z poziomu wspólnego języka C# / .NET code base. Aplikacje napisane przy użyciu platformy Xamarin można osiągnąć 75% do prawie 100% ponownego użycia kodu między platformami. Te aplikacje mają pełny dostęp do podstawowych interfejsów API platformy i może obejmować natywne interfejsy użytkownika. One kompilacji do specyficznych dla platformy pakietów z większego wpływu na wydajność środowiska uruchomieniowego. (Uwaga: program Xamarin obsługuje również F #, ale ta dokumentacja koncentruje się na C# tylko. Visual Basic nie jest obsługiwana w tej chwili.)

Deweloperzy zapoznać się z C# .NET i Visual Studio mogą używać tych samych możliwości i wydajność, podczas pracy z platformą Xamarin dla aplikacji mobilnych. Te korzyści to m.in. zdalne debugowanie na urządzeniach z systemem Android, iOS i Windows, bez konieczności uczenia się natywnych kodowania w językach Objective-C lub Java. Jest mały Zaskoczenie, a następnie oznacza wiele aplikacji o wysokiej wydajności przy użyciu projektowania atrakcyjnych interfejsów użytkownika — takie jak NASCAR, kierownik działu Aviva i MixRadio — utworzone za pomocą platformy Xamarin.

Ta dokumentacja pomoże Ci ocenić pełnych możliwości **programu Visual Studio za pomocą platformy Xamarin** do tworzenia tych środowisk.

-   Rozpoczynać [Instalator i instalacja](../cross-platform/setup-and-install.md), proces, który zajmie trochę czasu (zwykle 2 – 4 godzin w zależności od szybkości połączenia internetowego, co została już zainstalowana i wybrane opcje).

-   Gdy pliki instalacyjne są uruchomione, można [Dowiedz się więcej o programowaniu rozwiązań mobilnych za pomocą platformy Xamarin](learn-about-mobile-development-with-xamarin.md) który poinformuje o rodzaju Xamarin, porównaj zestawu narzędzi Xamarin.Forms do natywnego interfejsu użytkownika i nie tylko.

-   Po zakończeniu instalacji [Sprawdź swoje środowisko Xamarin](../cross-platform/verify-your-xamarin-environment.md).

-   Zakończ za pośrednictwem tego samouczka [opanowaniu podstaw tworzenia aplikacji przy użyciu zestawu narzędzi Xamarin.Forms w programie Visual Studio](learn-app-building-basics-with-xamarin-forms-in-visual-studio.md).

Możesz pracować z wszystkie funkcje platformy Xamarin przy użyciu [dowolnej wersji programu Visual Studio 2017](https://visualstudio.microsoft.com/vs) (Community, Professional i Enterprise). Nie osobnej licencji jest wymagana.

> [!NOTE]
>  Te instrukcje opisują konfigurację komputera Najłatwiejszym i najbardziej prostego dla deweloperów, którzy tło Windows i programu Visual Studio. W przypadku tej konfiguracji cały proces tworzenia jest uproszczone, ponieważ należy do interakcji z komputerem Mac, aby użyć symulatora systemu iOS i urządzenia powiązanego. Jeśli zamiast tego pochodzących z komputerów Mac w tle, firma Microsoft zaleca uruchamianie programu Visual Studio wewnątrz Parallels lub VMWare lub przy użyciu programu Visual Studio dla komputerów Mac. Zapoznaj się [Instalator, instalacja i weryfikacja dla użytkowników komputerów Mac](../cross-platform/setup-install-and-verifications-for-mac-users.md) instrukcje.

> [!NOTE]
>  Jeśli szukasz rozwiązanie programowanie dla wielu platform oparte na kodzie HTML i CSS, zapoznaj się z programu Visual Studio Tools for Apache Cordova zgodnie z opisem w [programowanie dla wielu platform w programie Visual Studio](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#HTML).