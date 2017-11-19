---
title: Shell (izolowany lub zintegrowany) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell
- Visual Studio, Shell
- Shell [Visual Studio]
- Visual Studio shell, shell-based applications
- Shell [Visual Studio], shell-based applications
ms.assetid: c64a9bf0-9bf8-45c3-8fa2-306fa6cab66a
caps.latest.revision: "25"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 92462699141f9d0a1af2d9eb461caadf4ee467ef
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="shell-isolated-or-integrated"></a>Shell (izolowany lub zintegrowany)
Można utworzyć własne aplikacji opartych na Visual Studio w trybie zintegrowanym lub izolowanej. W trybie zintegrowanym oprócz aplikacji dostępnych wiele funkcji programu Visual Studio. W trybie izolowanym wybierz polecenie podzbiór funkcji programu Visual Studio, które chcesz dystrybuować wraz z własne rozszerzenie.  
  
## <a name="integrated-mode"></a>Tryb zintegrowany  
 Tryb zintegrowany użytkownikom użyć standardowe funkcje programu Visual Studio razem z narzędziami niestandardowych. Powłoka w trybie zintegrowanym jest przeznaczony przede wszystkim do hostowania języków programowania i narzędzi rozwoju oprogramowania.  
  
 Scal narzędzi niestandardowych, które są tworzone automatycznie na powłoka w trybie zintegrowanym z dowolnej innej wersji programu Visual Studio jest zainstalowany na tym samym komputerze. Musisz podać powłoki programu Visual Studio zintegrowane w wersji redystrybucyjnej programu, jeśli nie zainstalowano jeszcze programu Visual Studio.  
  
 Powłoka programu Visual Studio zintegrowane w wersji redystrybucyjnej programu nie obejmuje programowania języków i funkcje, które obsługuje systemy odpowiednich projektu.  
  
> [!NOTE]
>  Tryb zintegrowany powłoki programu Visual Studio można zainstalować razem z wszystkich wersji programu Visual Studio z wyjątkiem wersji Express.  
  
 Aby uzyskać więcej informacji, zobacz [programu Visual Studio Shell (zintegrowany)](visual-studio-shell-integrated.md).  
  
## <a name="isolated-mode"></a>Tryb izolowany  
 Tryb izolowany służy do tworzenia niestandardowych narzędzi, które są uruchamiane side-by-side z innymi wersjami programu Visual Studio. Przewodnik jest przeznaczony głównie dla narzędzia, które mogą uzyskiwać dostęp do usługi Visual Studio bez w zależności od wszystkie standardowe funkcje programu Visual Studio. Można dostosować wygląd aplikacji utworzonych na powłoce programu Visual Studio samodzielnie. Można łatwo wyłączyć funkcje i grupy polecenia menu, które nie mają być wyświetlane razem z aplikacji.  
  
 Aby uzyskać więcej informacji, zobacz [programu Visual Studio Isolated Shell](visual-studio-isolated-shell.md).  
  
## <a name="distributing-your-integrated-or-isolated-shell-application"></a>Dystrybuowanie aplikacji zintegrowanego lub izolowane powłoki  
 Aby rozpowszechnić aplikacji zintegrowanego lub izolowane powłoki, należy to aplikacja, specjalne zintegrowanego lub izolowane powłoki pakietu redystrybucyjnego i program instalacyjny. Aby uzyskać więcej informacji na temat instalacji i dystrybucji, zobacz [dystrybucja aplikacje izolowane powłoki](distributing-isolated-shell-applications.md).  
  
> [!IMPORTANT]
>  [Umowy licencyjnej użytkownika końcowego (EULA)](https://www.visualstudio.com/en-us/support/legal/mt171552) dla programu Visual Studio zintegrowany i izolowane powłoki zawiera sekcja zbierania danych (**sekcji 3. Dane**).  Opisuje dane użycia klienta, które mogą być zbierane przez firmę Microsoft przez użytkowników albo zintegrowanego lub izolowane powłoki oprogramowania, które wkompilowania w aplikację. Aby uzyskać więcej informacji, zobacz [Microsoft Visual Studio produktów z rodziny Privacy Statement](https://www.visualstudio.com/en-us/dn948229).  
>   
>  W przypadku zbierania danych użycia osobnych od klientów za pośrednictwem aplikacji, należy podać użytkownikom stosowania można zbierać odpowiednie powiadomienie.  Podczas dystrybucji oprogramowania powłoki izolowanej lub zintegrowane jako część aplikacji, zgodnie z licencji programu Visual Studio SDK musi zawierać jedną z następujących czynności:  
>   
>  -   Umowa licencyjna użytkownika w ramach licencji aplikacji  
> -   własne umowy licencyjnej klientom wyrazić zgodę na warunki, które zapewniają ochronę programu Visual Studio wymaga zintegrowana lub izolowana powłoka co najmniej tyle jako postanowienia licencyjne programu Microsoft użytkownika końcowego dla oprogramowania powłoki  
  
## <a name="additional-resources"></a>Dodatkowe zasoby  
 Aby uzyskać więcej informacji na temat pakietów do dystrybucji, zobacz [Visual Studio Extensibility pliki do pobrania](http://go.microsoft.com/fwlink/?LinkID=119298) witryny sieci Web.  
  
## <a name="see-also"></a>Zobacz też  
 [Wysyłanie rozszerzeń programu Visual Studio](../shipping-visual-studio-extensions.md)