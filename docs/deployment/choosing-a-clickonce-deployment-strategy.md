---
title: Wybieranie strategii wdrażania ClickOnce | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, strategies
- deploying applications, ClickOnce
ms.assetid: 98bcab65-ab8b-4ed1-9adc-fdacf92b8106
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b811f194e0496030e1f46d1448736fb21f9579b3
ms.sourcegitcommit: b400528a83bea06d208d95c77282631ae4a93091
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2018
ms.locfileid: "34454730"
---
# <a name="choosing-a-clickonce-deployment-strategy"></a>Wybieranie strategii wdrażania ClickOnce
Istnieją trzy różne strategie wdrażania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji; strategii, która zależy przede wszystkim typu aplikacji, w której wdrażasz. Poniżej przedstawiono wszystkie trzy strategie wdrażania:  
  
-   Instalacja z sieci Web lub udziału sieciowego  
  
-   Instalacja z dysku CD  
  
-   Uruchamianie aplikacji z sieci Web lub udziału sieciowego  
  
    > [!NOTE]
    >  Oprócz wybrania strategii wdrażania, warto również wybrać strategię dostarczania aktualizacji aplikacji. Aby uzyskać więcej informacji, zobacz [Wybieranie strategii aktualizacji ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
## <a name="install-from-the-web-or-a-network-share"></a>Instalacja z sieci Web lub udziału sieciowego  
 Gdy jest używana ta strategia, aplikacja jest wdrażana na serwerze sieci Web lub w sieciowym udziale plików. Gdy użytkownik końcowy chce zainstalować aplikację, klika ikonę na stronie sieci Web lub klika dwukrotnie ikonę w udziale plików. Aplikacja jest następnie pobierana, instalowana i uruchamiana na komputerze użytkownika końcowego. Elementy są dodawane do **Start** menu i **Dodaj lub usuń programy** w **Panelu sterowania**.  
  
 Ta strategia jest zależna od połączeń sieciowych, więc sprawdza się najlepiej w przypadku aplikacji, które zostaną wdrożone dla użytkowników mających dostęp do sieci lokalnej lub szybkiego połączenia z Internetem.  
  
 W przypadku wdrażania aplikacji z sieci Web można przekazać argumenty do aplikacji podczas aktywowania jej za pomocą adresu URL. Aby uzyskać więcej informacji, zobacz [porady: pobieranie informacji o ciągu kwerendy w aplikacji ClickOnce w trybie Online](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md). Nie można przekazywać argumentów do aplikacji, która jest aktywowana za pomocą jednej z pozostałych metod opisanych w tym dokumencie.  
  
 Aby włączyć tej strategii wdrażania w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], kliknij przycisk **z sieci Web** lub **z UNC ścieżki lub w udziale plików** na **sposób instalacji** strony Kreatora publikacji.  
  
 Jest to domyślna strategia wdrażania.  
  
## <a name="start-the-application-from-the-web-or-a-network-share"></a>Uruchamianie aplikacji z sieci Web lub udziału sieciowego  
 Ta strategia jest podobna do pierwszej, z tym że aplikacja zachowuje się jak aplikacja sieci Web. Gdy użytkownik kliknie łącze na stronie sieci Web (lub kliknie dwukrotnie ikonę w udziale plików), aplikacja jest uruchamiana. Gdy użytkownicy Zamknij aplikację, nie jest już dostępny na komputerze lokalnym; nic nie jest dodane do **Start** menu lub **Dodaj lub usuń programy** w **Panelu sterowania**.  
  
> [!NOTE]
>  Technicznie aplikacja jest pobierana i instalowana w pamięci podręcznej aplikacji na komputerze lokalnym, tak samo jak aplikacja sieci Web jest pobierana do pamięci podręcznej sieci Web. Podobnie jak w przypadku pamięci podręcznej sieci Web, pliki są na końcu usuwane z pamięci podręcznej aplikacji. Jednak z punktu widzenia użytkownika aplikacja jest uruchamiana z sieci Web lub udziału plików.  
  
 Ta strategia najlepiej sprawdza się w przypadku aplikacji, które są rzadko używane, takich jak na przykład narzędzie do obliczania nagród dla pracowników, które zazwyczaj jest używane raz do roku.  
  
 Aby włączyć tej strategii wdrażania w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], kliknij przycisk **nie należy instalować aplikacji** na **instalacji lub uruchomić z sieci Web** strony Kreatora publikacji.  
  
 Aby ręcznie włączyć tej strategii wdrażania, zmień **zainstalować** tag w manifeście wdrażania. (Wartość może być **true** lub **false**. W Mage.exe, użyj **Online tylko** opcji **typu aplikacji** listy.)  

## <a name="install-from-a-cd"></a>Instalacja z dysku CD  
 Gdy jest używana ta strategia, aplikacja jest wdrażana na nośniku wymiennym, takim jak dysk CD-ROM lub DVD. W przypadku użycia poprzedniej opcji, gdy użytkownik wybierze opcję zainstalowania aplikacji, jest zainstalowana i uruchomiona, a elementy są dodawane do **Start** menu i **Dodaj lub usuń programy** w **formantu Panel**.  
  
 Ta strategia sprawdza się najlepiej w przypadku aplikacji wdrażanej dla użytkowników, którzy nie mają stałej łączności sieciowej lub używają połączeń o niskiej przepustowości. Aplikacja jest instalowana z nośnika wymiennego, więc do instalacji nie jest potrzebne połączenie sieciowe, jednak łączność sieciowa jest potrzebna do pobierania aktualizacji aplikacji.  
  
 Aby włączyć tej strategii wdrażania w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], kliknij przycisk **z dysku CD-ROM lub DVD-ROM** na **sposób instalacji** strony Kreatora publikacji.  
  
 Aby ręcznie włączyć tej strategii wdrażania, zmień **deploymentprovider —** tag w manifeście wdrażania. (W programie Visual Studio, ta właściwość jest ujawniona jako **URL instalacji** na **publikowania** strony projektanta projektu. W Mage.exe jest **Start lokalizacji**.)  
  
## <a name="web-browser-support"></a>Obsługa przeglądarek sieci Web  
 Aplikacje, których platformą docelową jest program .NET Framework 3.5, można zainstalować przy użyciu dowolnej przeglądarki.  
  
 Aplikacje, których platformą docelową jest program .NET Framework 2.0, wymagają programu Internet Explorer.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia ClickOnce i wdrażania](../deployment/clickonce-security-and-deployment.md)   
 [Wybieranie strategii aktualizacji ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Porady: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)