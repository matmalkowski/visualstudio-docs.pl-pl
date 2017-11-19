---
title: "Wdrażanie technologii ClickOnce do testowania i obsługi serwerów produkcyjnych bez ponownego podpisywania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, deploying without resigning
- ClickOnce deployment, without resigning
- application updates, ClickOnce
- update location [ClickOnce]
- deploymentProvider tag
- manifests [ClickOnce]
ms.assetid: 1218a98d-1ad5-4eef-95dd-0e0b3c44168c
caps.latest.revision: "10"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 91261e0bb70092861f216333bd73a11dc07790ba
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="deploying-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>Wdrażanie technologii ClickOnce do testowania i obsługi serwerów produkcyjnych bez ponownego podpisywania
W tym temacie omówiono nowa funkcja wprowadzona w programie .NET Framework w wersji 3.5, która umożliwia wdrażanie aplikacji ClickOnce z wielu lokalizacji sieciowych bez ponownego podpisywania lub zmiana ClickOnce manifesty ClickOnce.  
  
> [!NOTE]
>  Rezygnacja nadal jest to preferowana metoda wdrażania nowych wersji aplikacji. Jeśli to możliwe, należy użyć metody resigning. Aby uzyskać więcej informacji, zobacz [Mage.exe (Generowanie manifestu i edytowania narzędzie)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).  
  
 Deweloperów innych firm i niezależnym dostawcom oprogramowania można wyrazić zgodę na tej funkcji, co ułatwia klientom zaktualizować ich aplikacji. Ta funkcja może być używana w następujących sytuacjach:  
  
-   Podczas aktualizacji aplikacji, a nie pierwszej instalacji aplikacji.  
  
-   Jeśli istnieje tylko jedną konfigurację aplikacji na komputerze. Na przykład jeśli aplikacja jest skonfigurowana do punktu do dwóch różnych baz danych, nie można użyć tej funkcji.  
  
## <a name="excluding-deploymentprovider-from-deployment-manifests"></a>Deploymentprovider — wykluczanie manifesty wdrożenia  
 .NET Framework 2.0 i .NET Framework 3.0, należy określić dowolnej aplikacji ClickOnce, która instaluje na komputerze w trybie offline dostępność `deploymentProvider` w manifeście wdrażania. `deploymentProvider` Jest często określany jako lokalizacji aktualizacji; jest lokalizacja, w którym ClickOnce będzie sprawdzać dostępność aktualizacji aplikacji. To wymaganie, w połączeniu z konieczności wydawcy aplikacji i zarejestrować ich wdrożenia wprowadzone trudne do firmy można zaktualizować aplikacji ClickOnce od dostawcy lub innych firm. On również trudniejsza do wdrożenia tej samej aplikacji z wielu lokalizacji w tej samej sieci.  
  
 Zmiany dokonane w technologii ClickOnce w .NET Framework 3.5 istnieje możliwość innych firm w celu zapewnienia aplikacji ClickOnce do innej organizacji, której następnie można wdrożyć aplikację we własnej sieci.  
  
 Aby można było korzystać z tej funkcji, należy wykluczyć deweloperzy aplikacji ClickOnce `deploymentProvider` z ich wdrożenia manifesty. Oznacza to, z wyłączeniem `-providerUrl` argumentów podczas tworzenia wdrożenia manifesty Mage.exe lub upewnić się, **uruchamianie lokalizacji** pola tekstowego na **Manifest aplikacji** karta jest puste Jeśli możesz generowania manifesty wdrożenia z MageUI.exe.  
  
## <a name="deploymentprovider-and-application-updates"></a>deploymentprovider — i aktualizacje aplikacji  
 Począwszy od programu .NET Framework 3.5, nie trzeba określać `deploymentProvider` w manifeście wdrażania w celu wdrożenia aplikacji ClickOnce do użycia w trybie online i offline. Obsługuje ten scenariusz, w których należy spakować i samodzielnie zarejestrować wdrożenia, ale zezwala na innych firm wdrożyć aplikację w swoich sieciach.  
  
 Punkt klucza do zapamiętania jest to, że aplikacje, które wykluczyć `deploymentProvider` nie można zmienić ich lokalizacji instalacji podczas aktualizacji do momentu dostarczają aktualizacji, która zawiera `deploymentProvider` tagu ponownie.  
  
 Poniżej przedstawiono dwa przykłady wyjaśnienie tego punktu. W pierwszym przykładzie publikowania aplikacji ClickOnce, które nie ma `deploymentProvider` tag, a Poproś użytkowników, aby zainstalować go z http://www.adatum.com/MyApplication/. Jeśli zdecydujesz się, że chcesz opublikować na następną aktualizację aplikacji z http://subdomain.adatum.com/MyApplication/ zostanie nie ma możliwości programu oznaczający to w manifeście wdrażania, która znajduje się w http://www.adatum.com/MyApplication/. Możesz wybrać jedną z następujących operacji:  
  
-   Poproś użytkowników, aby odinstalować poprzednią wersję, a następnie zainstalować nową wersję z nowej lokalizacji.  
  
-   Aktualizacji na http://www.adatum.com/MyApplication/ zawierający `deploymentProvider` wskazujący http://www.adatum.com/MyApplication/. Zwolnij inną aktualizację później z `deploymentProvider` wskazujący http://subdomain.adatum.com/MyApplication/.  
  
 W drugim przykładzie publikowania aplikacji ClickOnce, która określa `deploymentProvider`, a następnie go usunąć. Raz nowej wersji bez `deploymentProvider` została pobrana do klientów, nie będzie mógł przekierowywać Ścieżka używana do aktualizacji do momentu wydania wersji aplikacji, która ma `deploymentProvider` przywrócona. Podobnie jak w pierwszym przykładzie `deploymentProvider` początkowo musi wskazywać bieżącą lokalizację aktualizacji nie nowej lokalizacji. W tym przypadku, jeśli próba wstawienia `deploymentProvider` odwołujący się do http://subdomain.adatum.com/MyApplication/, a następnie następnej aktualizacji zakończy się niepowodzeniem.  
  
## <a name="creating-a-deployment"></a>Tworzenie wdrożenia  
 Aby uzyskać instrukcje krok po kroku dotyczące tworzenia wdrożenia, które można wdrożyć w różnych lokalizacjach sieciowych, zobacz [wskazówki: ręczne wdrażanie aplikacji ClickOnce tego jest nie wymagają Re-Signing i że zachowuje informacje o znakowaniu](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Mage.exe (Generowanie manifestu i edytowania narzędzie)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [MageUI.exe (Generowanie manifestu i edytowania narzędzia, klient grafiki)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)