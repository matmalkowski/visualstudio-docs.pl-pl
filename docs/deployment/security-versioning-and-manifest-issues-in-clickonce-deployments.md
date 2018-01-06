---
title: "Zabezpieczenia, przechowywanie wersji i problemy z manifestami we wdrożeniach ClickOnce | Dokumentacja firmy Microsoft"
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
- versioning, ClickOnce applications
- ClickOnce applications, Windows Vista User Account Control
- ClickOnce applications, versioning issues
- security, ClickOnce applications
- Windows 7, ClickOnce deployments
- ClickOnce applications, manifest issues
- User Account Control, ClickOnce applications
- Windows Vista, ClickOnce deployments
- manifests [ClickOnce]
- ClickOnce applications, security issues
ms.assetid: d5d0c90b-ac1a-44e2-88dc-0d0ffd881624
caps.latest.revision: "21"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 53f9c0114573c6f08a2d9219e4dd2028ffe9ac7c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="security-versioning-and-manifest-issues-in-clickonce-deployments"></a>Zabezpieczenia, przechowywanie wersji i problemy z manifestami we wdrożeniach ClickOnce
Istnieją różne problemy z [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] zabezpieczeń, wersji aplikacji i składni manifestu i semantyki, która może spowodować [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia nie powiodło się.  
  
## <a name="clickonce-and-windows-vista-user-account-control"></a>ClickOnce i funkcję Kontrola konta użytkownika systemu Windows Vista  
 W [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)], aplikacje domyślnie są uruchamiane jako użytkownik standardowy, nawet jeśli bieżący użytkownik jest zalogowany przy użyciu konta z uprawnieniami administratora. Jeśli aplikacja musi wykonać akcję, która musi mieć uprawnienia administratora, informuje system operacyjny, który następnie monituje użytkownika o wprowadzenie poświadczeń administratora. Tej funkcji, która ma nazwę kontroli konta użytkownika (UAC), uniemożliwia aplikacji wprowadzania zmian, które mogą mieć wpływ na cały system operacyjny bez wyraźnej zgody użytkownika. Aplikacje systemu Windows zadeklarować potrzebują tego podniesienia uprawnień, określając `requestedExecutionLevel` atrybutu w `trustInfo` części w manifeście aplikacji.  
  
 Z powodu ryzyka związanego z ujawnieniem aplikacji na ataki podniesienia uprawnień zabezpieczeń [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji nie można żądać podniesienia uprawnień, jeśli włączono kontrolę konta użytkownika dla klienta. Wszelkie [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji, która próbuje ustawić jej `requestedExecutionLevel` atrybutu `requireAdministrator` lub `highestAvailable` nie zostaną zainstalowane na [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)].  
  
 W niektórych przypadkach z [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacja może spróbować uruchomić z uprawnieniami administratora z powodu logikę wykrywania Instalatora na [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)]. W takim przypadku można ustawić `requestedExecutionLevel` atrybutu w manifeście aplikacji do `asInvoker`. To spowoduje, że aplikację można uruchomić bez podniesienia uprawnień. [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)]automatycznie dodaje atrybut do wszystkich manifestów aplikacji.  
  
 Jeśli tworzysz aplikację, która wymaga uprawnień administratora przez cały czas ich istnienia aplikacji, należy rozważyć wdrożenie aplikacji przy użyciu technologii Instalatora Windows (MSI), zamiast tego. Aby uzyskać więcej informacji, zobacz [podstawy Instalatora systemu Windows](../extensibility/internals/windows-installer-basics.md).  
  
## <a name="online-application-quotas-and-partial-trust-applications"></a>Przydziały aplikacji online i częściowego zaufania aplikacji  
 Jeśli Twoje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacja jest uruchamiana online, a nie za pomocą instalacji, musi mieścić się w przydziału dla aplikacji online. Ponadto aplikacji sieciowej, która działa w częściowej relacji zaufania, takich jak z ograniczonym zestawem uprawnień zabezpieczeń, nie może przekraczać połowy rozmiaru przydziału.  
  
 Aby uzyskać więcej informacji i dowiedzieć się, jak zmienić przydział aplikacji online, zobacz [Przegląd pamięci podręcznej ClickOnce](../deployment/clickonce-cache-overview.md).  
  
## <a name="versioning-issues"></a>Problemy z wersjonowaniem  
 Jeśli zostanie przypisana do używanego zestawu silnych nazw zwiększenie numeru wersji zestawu do uwzględnienia aktualizacji aplikacji, mogą wystąpić problemy. Wszelkie zestawu skompilowanego z odwołaniem do zestawu z silną nazwą musi się ponownie skompilowana, lub zestawu próbuje odwołać starszej wersji. Zestaw spróbuje to, ponieważ zestaw używa stara wartość wersji w swoim żądaniu powiązania.  
  
 Załóżmy, że zostały zestawu z silną nazwą własnego projektu w wersji 1.0.0.0. Po kompilacji zestawu, Dodaj jako odwołanie do projektu, który zawiera głównej aplikacji. Jeśli aktualizacja zestawu, zwiększyć tę wersję 1.0.0.1 i spróbuj wdrożyć ją bez również ponowną kompilację aplikacji aplikacji nie będzie można załadować zestawu w czasie wykonywania.  
  
 Ten błąd może wystąpić tylko wtedy, gdy edytujesz Twojej [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ręcznie; manifesty nie powinna występować ten błąd, jeśli generowane przy użyciu wdrożenia [!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)].  
  
## <a name="specifying-individual-net-framework-assemblies-in-the-manifest"></a>Określenie poszczególnych .NET Framework zestawów w manifeście  
 Aplikacja nie będzie można załadować, jeśli dokonano ręcznej edycji [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia, aby odwołać starszej wersji [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] zestawu. Na przykład dodać odwołanie do zestawu System.Net wersji [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] przed wersja określona w manifeście, następnie może wystąpić błąd. Ogólnie rzecz biorąc, należy zrezygnować do określenia odniesienia do poszczególnych [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] zestawy, jako wersja [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] względem której aplikacja działa jest określony jako zależności w manifeście aplikacji.  
  
## <a name="manifest-parsing-issues"></a>Manifest analizowania problemów  
 Pliki manifestu, które są używane przez [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] są plikami XML i muszą być zarówno poprawnie sformułowany i prawidłową: muszą przestrzegać reguły składni XML i używać tylko elementy i atrybuty zdefiniowane w odpowiednich schematu XML.  
  
 Coś, co może spowodować problemy w pliku manifestu jest wybranie nazwę aplikacji, która zawiera znaki specjalne, takie jak cudzysłowem pojedynczym lub podwójnym. Nazwa aplikacji jest częścią jego [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] tożsamości. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]obecnie nie przeanalizować tożsamości, które zawierają znaki specjalne. Jeśli aplikacja nie może aktywować, upewnij się, przy użyciu tylko alfabetyczne, cyfry, znaki dla nazwy i ponów próbę jej wdrożenia ponownie.  
  
 Jeśli dokonano ręcznej edycji manifestów Twoje wdrożenia lub aplikacji, należy mieć przypadkowo uszkodzony je. Manifest uszkodzony uniemożliwi poprawne [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] instalacji. Można debugować takie błędy w czasie wykonywania, klikając **szczegóły** na **błąd ClickOnce** okno dialogowe i odczytywania komunikat o błędzie w dzienniku. Dziennik będzie listy jedną z następujących komunikatów:  
  
-   Opis błąd składniowy, numer wiersza i znaku położenie, w którym wystąpił błąd.  
  
-   Nazwa elementu lub atrybutu używanego w naruszenie schematu manifestu. Dodano XML ręcznie do Twojej manifestów, należy porównać swoje dodatki do manifestu schematów. Aby uzyskać więcej informacji, zobacz [Manifest wdrażania ClickOnce](../deployment/clickonce-deployment-manifest.md) i [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md).  
  
-   Wystąpi konflikt identyfikatorów. Odwołań do zależności w manifesty wdrażania i aplikacji musi być unikatowa w obu ich `name` i `publicKeyToken` atrybutów. Jeśli oba atrybuty są zgodne między dwoma elementami, które w manifeście, analizowanie manifestu nie powiedzie się.  
  
## <a name="precautions-when-manually-changing-manifests-or-applications"></a>Środki ostrożności podczas ręcznej zmiany manifesty lub aplikacji  
 Po zaktualizowaniu manifest aplikacji, należy ponownie podpisać zarówno manifest aplikacji i manifest wdrażania. Manifest rozmieszczenia zawiera odwołanie do manifestu aplikacji, czy plik skrótu i podpis cyfrowy.  
  
### <a name="precautions-with-deployment-provider-usage"></a>Środki ostrożności z użycia dostawcy wdrożenia  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Manifeście rozmieszczenia `deploymentProvider` właściwość, która wskazuje na pełną ścieżkę lokalizacji, z którym zainstalowane i obsługiwać aplikacji:  
  
```  
<deploymentProvider codebase="http://myserver/myapp.application" />  
```  
  
 Ta ścieżka jest ustawiana podczas [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] tworzy aplikację i jest obowiązkowa w przypadku zainstalowanych aplikacji. Ścieżka wskazuje standardowe miejsce gdzie [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Instalator zainstaluje aplikację i wyszukaj aktualizacje. Jeśli używasz **xcopy** polecenie, aby skopiować [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji w innej lokalizacji, ale nie należy zmieniać `deploymentProvider` właściwość [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] będą nadal odwołują się do oryginalnej lokalizacji podczas próby pobrania aplikacja.  
  
 Jeśli chcesz przenieść lub skopiować aplikacji, należy również zaktualizować `deploymentProvider` ścieżki, tak aby rzeczywiście instalacji klienta z nowej lokalizacji. Ta ścieżka jest aktualizowanie przede wszystkim problemem po zainstalowaniu aplikacji. Dla aplikacji online, które są zawsze uruchamiane przy użyciu oryginalnego adresu URL, ustawienie `deploymentProvider` jest opcjonalna. Jeśli `deploymentProvider` jest ustawiona, będą honorowane; w przeciwnym razie adres URL używany do uruchomienia aplikacji będzie służyć jako podstawowy adres URL do pobrania plików aplikacji.  
  
> [!NOTE]
>  Zawsze zaktualizowanie manifestu musisz również zarejestrować go ponownie.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozwiązywanie problemów z wdrożeniami ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)   
 [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Wybieranie strategii wdrażania ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)