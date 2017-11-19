---
title: "Wymagania wstępne dotyczące wdrażania aplikacji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, platform detection
- ClickOnce deployment, prerequisites
- ClickOnce deployment, dependencies
- prerequisites, ClickOnce
- dependencies, ClickOnce
ms.assetid: fc6e047e-ad94-44e8-8ff5-b6d1f4ca7735
caps.latest.revision: "51"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: c323e3800e98e2451a371f3ff84b3351d760a94c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="application-deployment-prerequisites"></a>Wstępnie wymagane składniki wdrażania aplikacji
Aby upewnić się, że aplikacja będzie zainstalować i uruchomić pomyślnie, należy najpierw upewnić, że wszystkie składniki, od których zależy aplikacja są już zainstalowane na komputerze docelowym. Na przykład większość aplikacji utworzony za pomocą [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zależy od [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]; poprawną wersję środowiska CLR musi być obecny na komputerze docelowym, przed zainstalowaniem aplikacji.  
  
 Można wybrać te wymagania wstępne w **wstępnie wymagane składniki — okno dialogowe** i zainstalować w ramach instalacji programu .NET Framework i innych pakietów redystrybucyjnych. Takie rozwiązanie jest nazywany *uruchamianie*. Następnie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] generuje program wykonywalny systemu Windows o nazwie Setup.exe, znanej także jako *programu inicjującego*. Program inicjujący jest odpowiedzialny za instalowanie wymagań wstępnych przed uruchomieniem Twojej aplikacji. Aby uzyskać więcej informacji o wybieraniu wymagań wstępnych, zobacz [wstępnie wymagane składniki — okno dialogowe](../ide/reference/prerequisites-dialog-box.md).  
  
 Każdy warunkiem wstępnym jest pakiet programu inicjującego. Pakiet programu inicjującego to grupa katalogów i plików, które zawierają pliki manifestu, które opisują sposób instalacji wymagań wstępnych. Jeśli wymagania wstępne dotyczące Twojej aplikacji nie są wymienione w **wymagań wstępnych okno dialogowe**, można tworzyć niestandardowe pakiety programu inicjującego i dodaj je do programu Visual Studio. Można wybrać wymagania wstępne w **wstępnie wymagane składniki — okno dialogowe**. Aby uzyskać więcej informacji, zobacz [tworzenie pakietów programu inicjującego](../deployment/creating-bootstrapper-packages.md).  
  
 Domyślnie ładowania jest włączona dla wdrożenia ClickOnce. Wygenerowany dla wdrażania ClickOnce inicjujący jest podpisana. Możesz wyłączyć uruchamianie do składnika, ale należy zrobić to tylko wtedy, gdy masz pewność, że poprawna wersja składnika jest już zainstalowana na wszystkich komputerach docelowych.  
  
## <a name="bootstrapping-and-clickonce-deployment"></a>Uruchamianie i wdrażania ClickOnce  
 Przed zainstalowaniem aplikacji na komputerze klienckim [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] zbada klienta, aby upewnić się, że aplikacja ma określone wymagania określone w manifeście aplikacji. Należą do nich między innymi:  
  
-   Minimalna wymagana wersja środowiska CLR, które jest określone jako zależność zestawu w manifeście aplikacji.  
  
-   Minimalna wymagana wersja systemu operacyjnego Windows, które są wymagane przez aplikację, jak określono w aplikacji manifestu przy użyciu `<osVersionInfo>` elementu. (Zobacz [ \<zależności > elementu](../deployment/dependency-element-clickonce-application.md))  
  
-   Minimalna wersja wszystkie zestawy, które muszą być wstępnie zainstalowane w globalnej pamięci podręcznej zestawów (GAC), jak określono w zestawie zależności deklaracji w manifeście zestawu.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]wykrywa brakujące wymagania wstępne i wymagania wstępne można zainstalować za pomocą programu inicjującego. Aby uzyskać więcej informacji, zobacz [porady: instalowanie wstępnie wymaganych składników w aplikacji ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md).  
  
> [!NOTE]
>  Aby zmienić wartości w manifestach wygenerowane za pomocą narzędzi takich jak [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i MageUI.exe, należy edytować manifest aplikacji w edytorze tekstów i ponowne podpisywanie manifestów aplikacji i wdrażania. Aby uzyskać więcej informacji, zobacz [porady: ponowne podpisywanie aplikacji i manifestów wdrożenia](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
 Jeśli używasz programu Visual Studio i ClickOnce do wdrażania aplikacji, pakietów programu inicjującego, które są wybrane domyślnie są zależne od wersji programu .NET Framework w rozwiązaniu. Jednak jeśli należy zmienić docelową wersję platformy .NET, należy zaktualizować opcje w **wstępnie wymagane składniki — okno dialogowe** ręcznie.  
  
|Docelowy .NET Framework|Pakiety programu inicjującego wybranych|  
|---------------------------|------------------------------------|  
|.NET Framework 4 Client Profile|.NET Framework 4 Client Profile<br /><br /> Instalator Windows 3.1|  
|Program .NET Framework 4|Program .NET Framework 4<br /><br /> Instalator Windows 3.1|  
  
 Z [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia, generowane przez stronę Publish.htm [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Kreator publikowania punktów albo łącze, które instaluje tylko aplikację lub do łącza instalowane zarówno aplikacji i składników bootstrapped.  
  
 Jeśli program inicjujący generowane przy użyciu Kreatora publikacji ClickOnce lub opublikuj stronę w programie Visual Studio, Setup.exe automatycznie jest podpisana. Jednak jeśli chcesz używać certyfikatów klienta do podpisania program inicjujący można podpisać plik później.  
  
## <a name="bootstrapping-and-msbuild"></a>Uruchamianie i MSBuild  
 Jeśli nie używasz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ale kompilowania aplikacji w wierszu polecenia, można utworzyć [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Inicjowanie aplikacji za pomocą zadania kompilacji Engine (MSBuild) firmy Microsoft. Aby uzyskać więcej informacji, zobacz [generatebootstrapper — zadanie](../msbuild/generatebootstrapper-task.md).  
  
 Alternatywą wobec uruchamianie wstępnie składniki można wdrożyć przy użyciu systemu dystrybucji oprogramowania elektronicznych, takich jak Microsoft Systems Management Server (SMS).  
  
## <a name="bootstrapper-setupexe-command-line-arguments"></a>Argumenty wiersza polecenia programu inicjującego (Setup.exe)  
 Setup.exe generowane przez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i zadania programu MSBuild obsługuje niewielki zestaw następujące argumenty wiersza polecenia. Argumenty do bootstrapping aplikacji innych niż te są przekazywane do Instalatora aplikacji.  
  
 Jeśli zmienisz żadnych opcji programu inicjującego musi Zmień inicjujący bez znaku i następnie zarejestrować plik inicjujący później.  
  
|Argument wiersza polecenia|Opis|  
|---------------------------|-----------------|  
|**-?, -h, — pomoc**|Wyświetla okno dialogowe Pomoc.|  
|**— adres url, - componentsurl**|Pokazuje przechowywanych adresu URL i adresu url składników dla tego zestawu w górę.|  
|**-url =**`location`|Ustawia adres URL, w którym będzie szukać Setup.exe [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji.|  
|**-componentsurl =**`location`|Ustawia adres URL, w którym Setup.exe będzie szukać zależności, takich jak [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].|  
|**-homesite =** `true` **&#124;**`false`|Gdy `true`, pliki do pobrania zależności z preferowanych lokalizacji dostawcy witryny. Przesłania **- componentsurl** ustawienie. Gdy `false`, pliki do pobrania zależności z adresu URL określonego przez **- componentsurl**.|  
  
## <a name="operating-system-support"></a>Obsługa systemu operacyjnego  
 Inicjujący Instalatora programu Visual Studio nie jest obsługiwana instalacja Server Core systemu Windows Server 2008 lub Windows Server 2008 R2 Server Core, będące środowisku małej konserwacji serwera z ograniczoną funkcjonalnością. Na przykład opcja instalacji Server Core obsługuje tylko profilu .NET Framework 3.5 Server Core, więc nie można uruchomić funkcji programu Visual Studio, które są zależne od pełnego .NET Framework.  
  
## <a name="see-also"></a>Zobacz też  
 [Wybieranie strategii wdrażania ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [Zabezpieczenia ClickOnce i wdrażania](../deployment/clickonce-security-and-deployment.md)