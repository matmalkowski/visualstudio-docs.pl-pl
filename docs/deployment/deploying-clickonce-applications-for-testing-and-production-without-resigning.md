---
title: Wdrażanie technologii ClickOnce do testowania i obsługi serwerów produkcyjnych bez ponownego podpisywania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 57b4761ed7f0b223e459fc1ac77ad93c546e02dc
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="deploying-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>Wdrażanie technologii ClickOnce do testowania i obsługi serwerów produkcyjnych bez ponownego podpisywania
W tym artykule opisano funkcji wprowadzonych w programie .NET Framework w wersji 3.5, która umożliwia wdrażanie aplikacji ClickOnce z wielu lokalizacji sieciowych bez ponownego podpisywania lub zmiana ClickOnce manifesty ClickOnce.  
  
> [!NOTE]
>  Rezygnacja nadal jest to preferowana metoda wdrażania nowych wersji aplikacji. Jeśli to możliwe, należy użyć metody resigning. Aby uzyskać więcej informacji, zobacz [Mage.exe (Generowanie manifestu i edytowania narzędzie)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).  
  
 Deweloperzy innych firm i niezależnym dostawcom oprogramowania zgodzić się na tej funkcji, co ułatwia klientom zaktualizować swoje aplikacje. Ta funkcja może być używana w następujących sytuacjach:  
  
-   Podczas aktualizacji aplikacji, nie dla pierwszej instalacji aplikacji.  
  
-   Jeśli istnieje tylko jedną konfigurację aplikacji na komputerze. Na przykład jeśli aplikacja jest skonfigurowana do punktu do dwóch różnych baz danych, nie można użyć tej funkcji.  
  
## <a name="excluding-deploymentprovider-from-deployment-manifests"></a>Deploymentprovider — wykluczanie manifesty wdrożenia  
 .NET Framework 2.0 i .NET Framework 3.0 musi zawierać dowolnej aplikacji ClickOnce, która instaluje na komputerze w trybie offline dostępność `deploymentProvider` w manifeście wdrażania. `deploymentProvider` Jest często określany jako lokalizacji aktualizacji; jest lokalizacja, w którym ClickOnce sprawdzania aktualizacji aplikacji. To wymaganie, wraz z konieczności wydawcy aplikacji i zarejestrować ich wdrożenia wprowadzone trudne do firmy można zaktualizować aplikacji ClickOnce od dostawcy lub inne innych firm. On również trudniejsza do wdrożenia tej samej aplikacji z wielu lokalizacji w tej samej sieci.  
  
 Zmiany dokonane w technologii ClickOnce w .NET Framework 3.5 istnieje możliwość innych firm w celu zapewnienia aplikacji ClickOnce do innej organizacji, której następnie można wdrożyć aplikację we własnej sieci.  
  
 Aby można było korzystać z tej funkcji, należy wykluczyć deweloperzy aplikacji ClickOnce `deploymentProvider` z ich wdrożenia manifesty. Wymaganie to oznacza, że należy wykluczyć `-providerUrl` argumentów podczas tworzenia wdrożenia manifesty z Mage.exe. Lub, jeśli manifesty wdrożenia z MageUI.exe jest generowany, użytkownik musi upewnij się, że **uruchamianie lokalizacji** pola tekstowego na **Manifest aplikacji** karta jest puste.  
  
## <a name="deploymentprovider-and-application-updates"></a>deploymentprovider — i aktualizacje aplikacji  
 Począwszy od programu .NET Framework 3.5, nie trzeba określać `deploymentProvider` w manifeście wdrażania w celu wdrożenia aplikacji ClickOnce do użycia w trybie online i offline. Ta zmiana obsługuje scenariusz, w których należy spakować i samodzielnie zarejestrować wdrożenia, ale zezwala na innych firm wdrożyć aplikację w swoich sieciach.  
  
 Należy koniecznie zwrócić do zapamiętania jest to, że aplikacje, które wykluczyć `deploymentProvider` nie można zmienić ich lokalizacji instalacji podczas aktualizacji do momentu dostarczają aktualizacji, która zawiera `deploymentProvider` tagu ponownie.  
  
 Poniżej przedstawiono dwa przykłady wyjaśnienie tego punktu. W pierwszym przykładzie publikowania aplikacji ClickOnce, które nie ma `deploymentProvider` znaczników i poproś użytkowników o zainstaluj ją z http://www.adatum.com/MyApplication/. Jeśli zdecydujesz, którą chcesz opublikować na następną aktualizację aplikacji z http://subdomain.adatum.com/MyApplication/, użytkownik nie ma możliwości oznaczający to w manifeście wdrażania, która znajduje się w http://www.adatum.com/MyApplication/. Możesz wybrać jedną z następujących operacji:  
  
-   Poproś użytkowników, aby odinstalować poprzednią wersję, a następnie zainstalować nową wersję z nowej lokalizacji.  
  
-   Uwzględnić aktualizację na http://www.adatum.com/MyApplication/ zawierającą `deploymentProvider` wskazujący http://www.adatum.com/MyApplication/. Zwolnij inną aktualizację później z `deploymentProvider` wskazujący http://subdomain.adatum.com/MyApplication/.  
  
 W drugim przykładzie publikowania aplikacji ClickOnce, która określa `deploymentProvider`, a następnie go usunąć. Raz nowej wersji bez `deploymentProvider` zostanie pobrana do klientów, nie można przekierować Ścieżka używana do aktualizacji do momentu wydania wersji aplikacji, która ma `deploymentProvider` przywrócona. Podobnie jak w pierwszym przykładzie `deploymentProvider` początkowo musi wskazywać bieżącą lokalizację aktualizacji nie nowej lokalizacji. W tym przypadku, jeśli próba wstawienia `deploymentProvider` odwołujący się do http://subdomain.adatum.com/MyApplication/, Następna aktualizacja zakończy się niepowodzeniem.  
  
## <a name="creating-a-deployment"></a>Tworzenie wdrożenia  
 Aby uzyskać instrukcje krok po kroku dotyczące tworzenia wdrożenia, które można wdrożyć w różnych lokalizacjach sieciowych, zobacz [wskazówki: ręczne wdrażanie aplikacji ClickOnce tego jest nie wymagają Re-Signing i że zachowuje informacje o znakowaniu](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Mage.exe (Generowanie manifestu i edytowania narzędzie)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [MageUI.exe (narzędzie generowania i edytowania manifestu, klient z interfejsem graficznym)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)