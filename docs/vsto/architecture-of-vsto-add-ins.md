---
title: "Architektura dodatków narzędzi VSTO | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VSTOLoader.dll
- architecture [Office development in Visual Studio], application-level add-ins
- vstoee.dll
- application-level add-ins [Office development in Visual Studio], architecture
- add-ins [Office development in Visual Studio], architecture
ms.assetid: 978f102f-15c6-44e4-84e8-80b161408324
caps.latest.revision: "70"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: a4dbe8611da0814bfaa148b2d9c4caf7f7858d9d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="architecture-of-vsto-add-ins"></a>Architektura dodatków narzędzi VSTO
  Dodatków VSTO utworzone za pomocą narzędzia Office developer tools w programie Visual Studio architektury funkcjami, które wyróżnić stabilności i zabezpieczeń, a następnie włącz je, aby ściśle współpracować z programem Microsoft Office. W tym temacie opisano następujące aspekty dodatków VSTO:  
  
-   [Opis dodatków VSTO](#UnderstandingAddIns)  
  
-   [Składniki dodatków VSTO](#AddinComponents)  
  
-   [Jak działają dodatków VSTO z aplikacji Microsoft Office](#HowAddinsWork)  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
 Aby uzyskać ogólne informacje o tworzeniu dodatków VSTO, zobacz [rozwój rozwiązań Office ― omówienie &#40; VSTO &#41; ](../vsto/office-solutions-development-overview-vsto.md) i [wprowadzenie do programowania dodatków narzędzi VSTO](../vsto/getting-started-programming-vsto-add-ins.md).  
  
##  <a name="UnderstandingAddIns"></a>Opis dodatków VSTO  
 Korzystając z narzędzia Office developer tools w programie Visual Studio do tworzenia dodatku VSTO, możesz utworzyć zestawu zarządzanego kodu, który jest ładowany przez aplikację Microsoft Office. Po zestaw jest ładowany, dodatku VSTO może odpowiadać na zdarzenia, które są generowane w aplikacji (na przykład po kliknięciu elementu menu). Dodatku VSTO także wywołać object model automatyzacji i rozszerzenie aplikacji i może używać dowolnej klasy w [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)].  
  
 Zestaw komunikuje się z aplikacji składników COM za pomocą podstawowego zestawu międzyoperacyjnego aplikacji. Aby uzyskać więcej informacji, zobacz [podstawowe zestawy międzyoperacyjne pakietu Office](../vsto/office-primary-interop-assemblies.md) i [rozwój rozwiązań Office ― omówienie &#40; VSTO &#41; ](../vsto/office-solutions-development-overview-vsto.md).  
  
 W przypadku instalowania wielu dodatków narzędzi VSTO dla aplikacji każdy dodatek VSTO jest ładowany w domenie innej aplikacji. Oznacza to, że jeden VSTO dodatek, który zachowuje się niepoprawnie nie może spowodować innych VSTO dodatki się niepowodzeniem. Pomaga również upewnij się, że po zamknięciu aplikacji wszystkie dodatku VSTO zestawy są usuwane z pamięci. Aby uzyskać więcej informacji o domenach aplikacji, zobacz [domen aplikacji](/dotnet/framework/app-domains/application-domains).  
  
> [!NOTE]  
>  Dodatków VSTO, utworzonych przy użyciu programu Visual Studio Office developer tools są przeznaczone do użycia tylko wtedy, gdy host aplikacji Microsoft Office jest uruchomiona przez użytkownika końcowego. Jeśli aplikacja jest uruchomiona programowo (na przykład przy użyciu automatyzacji), dodatku VSTO może nie działać zgodnie z oczekiwaniami.  
  
##  <a name="AddinComponents"></a>Składniki dodatków VSTO  
 Chociaż zestaw dodatku VSTO jest głównym składnikiem, istnieje kilka składników, które odgrywa ważną rolę w sposób aplikacji Microsoft Office odnaleźć i załadować dodatków narzędzi VSTO.  
  
### <a name="registry-entries"></a>Wpisy rejestru  
 Aplikacje Microsoft Office odnajdywanie dodatków VSTO, wyszukując zbiór wpisów rejestru. Pełną listę wpisy rejestru używany przez dodatki VSTO zobacz [wpisy rejestru dotyczące dodatków narzędzi VSTO](../vsto/registry-entries-for-vsto-add-ins.md).  
  
 Podczas kompilowania rozwiązania Visual Studio tworzy wszystkie wpisy rejestru wymagane na komputerze dewelopera, można debugowania i uruchamiania programu dodatku VSTO. Aby uzyskać więcej informacji, zobacz [kompilowanie rozwiązań pakietu Office](../vsto/building-office-solutions.md).  
  
 Jeśli używasz ClickOnce do wdrażania rozwiązania, Instalator automatycznie wygenerowanych przez proces publikowania tworzy klucze rejestru na komputerze użytkownika końcowego. Aby uzyskać więcej informacji, zobacz [wdrażania rozwiązania do pakietu Office za pomocą technologii ClickOnce za pomocą](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
### <a name="deployment-manifest-and-application-manifest"></a>Manifest rozmieszczenia i Manifest aplikacji  
 Dodatków VSTO Użyj manifesty wdrożenia i manifestów aplikacji do identyfikowania i załadować najnowszej wersji zestawu dodatku VSTO. Wdrożenie manifestu wskazuje bieżący manifest aplikacji. Manifest aplikacji wskazuje zestaw dodatku VSTO i określa klasę punktu wejścia do wykonania w zestawie. Aby uzyskać więcej informacji, zobacz [manifesty wdrożenia w rozwiązaniach pakietu Office i aplikacji](../vsto/application-and-deployment-manifests-in-office-solutions.md).  
  
### <a name="visual-studio-tools-for-office-runtime"></a>Visual Studio Tools for Office Runtime  
 Aby uruchomić dodatków VSTO, które są tworzone za pomocą narzędzia Office developer tools w programie Visual Studio, użytkownik końcowy komputery muszą mieć [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] zainstalowane. Środowisko uruchomieniowe zawiera składniki niezarządzane i zestaw zarządzanych zestawów. Składnik niezarządzany załadować zestawu dodatku VSTO. Zarządzanych zestawów Podaj model obiektu, który używa Twój kod dodatku VSTO zautomatyzować i rozszerzenie aplikacji hosta.  
  
 Aby uzyskać więcej informacji, zobacz [Visual Studio Tools for Office Runtime ― Przegląd](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
##  <a name="HowAddinsWork"></a>Jak działają dodatkach VSTO z aplikacjami pakietu Microsoft Office  
 Gdy użytkownik uruchamia aplikację Microsoft Office, aplikacja używa manifest wdrażania i manifest aplikacji do lokalizowania i ładowania najnowszej wersji zestawu dodatku VSTO. Na poniższej ilustracji przedstawiono podstawowej architektury tych dodatków VSTO.  
  
 ![Architektura dodatków pakietu office 2007](../vsto/media/office07addin.png "Architektura dodatków pakietu Office 2007")  
  
> [!NOTE]  
>  W rozwiązaniach pakietu Office, które odnoszą się do [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], rozwiązań wywołanie object model aplikacji hosta przez przy użyciu informacji o typie PIA, który jest osadzony w zestawie rozwiązania, zamiast wywoływać metodę do PIA bezpośrednio. Aby uzyskać więcej informacji, zobacz [projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md).  
  
### <a name="loading-process"></a>Proces ładowania  
 Gdy użytkownik uruchamia aplikację, wykonywane są następujące kroki:  
  
1.  Aplikacja sprawdza w rejestrze wpisy, które identyfikują dodatków VSTO, które zostały utworzone przy użyciu narzędzia Office developer tools w programie Visual Studio.  
  
2.  Jeśli aplikacja znajdzie te wpisy rejestru, VSTOEE.dll, który jest ładowany VSTOLoader.dll ładowania aplikacji. Są to niezarządzanych bibliotek DLL, które są składnikami modułu ładującego dla Visual Studio 2010 Tools for Office Runtime. Aby uzyskać więcej informacji, zobacz [Visual Studio Tools for Office Runtime ― Przegląd](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
3.  Ładuje VSTOLoader.dll [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] i uruchamia zarządzanych część [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
4.  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Sprawdza dostępność aktualizacji manifestu i pliki do pobrania najnowszych manifestów aplikacji i wdrażania.  
  
5.  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Wykonuje szereg kontroli zabezpieczeń. Aby uzyskać więcej informacji, zobacz [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md).  
  
6.  Jeśli dodatku VSTO jest zaufany do uruchomienia, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] używa manifest wdrażania i manifest aplikacji do sprawdzania aktualizacji zestawu. Jeśli dostępna jest nowa wersja zestawu, środowisko uruchomieniowe pobiera nowej wersji zestawu do [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] pamięci podręcznej na komputerze klienckim. Aby uzyskać więcej informacji, zobacz [wdrażania rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md).  
  
7.  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Tworzy nową domenę aplikacji, w którym można załadować zestawu dodatku VSTO.  
  
8.  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Ładuje zestaw dodatku VSTO do domeny aplikacji.  
  
9. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Wywołania <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> metoda VSTO dodatek, jeśli zostały zastąpione go.  
  
     Opcjonalnie można zastąpić tę metodę, aby ujawnić obiektu w Twojej dodatku VSTO do innych rozwiązań Microsoft Office. Aby uzyskać więcej informacji, zobacz [wywoływanie kodu w dodatkach VSTO z innych rozwiązań pakietu Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).  
  
10. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Wywołania <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> metoda VSTO dodatek, jeśli zostały zastąpione go.  
  
     Opcjonalnie można zastąpić tę metodę, aby rozszerzyć pakietu Microsoft Office, zwracając obiekt, który implementuje interfejs rozszerzalności. Aby uzyskać więcej informacji, zobacz [Dostosowywanie interfejsu użytkownika funkcji przez przy użyciu rozszerzalności interfejsów](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md).  
  
    > [!NOTE]  
    >  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Sprawia, że oddzielne wywołań <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> metody dla każdego interfejsu rozszerzalności, która jest obsługiwana przez aplikację hosta. Mimo że pierwsze wywołanie <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> metody zazwyczaj miejsce przed wywołaniem do `ThisAddIn_Startup` metody, dodatek VSTO, nie należy wprowadzać żadnych założeń o tym, kiedy <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> metoda zostanie wywołana lub ile razy zostanie wywołany.  
  
11. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Wywołania `ThisAddIn_Startup` w dodatku VSTO z metody. Ta metoda jest domyślny program obsługi zdarzeń dla <xref:Microsoft.Office.Tools.AddInBase.Startup> zdarzeń. Aby uzyskać więcej informacji, zobacz [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Architektura rozwiązań pakietu Office w Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)   
 [Architektura Dostosowywanie na poziomie dokumentu](../vsto/architecture-of-document-level-customizations.md)   
 [Visual Studio Tools for Office Runtime ― Przegląd](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Programowanie dodatków VSTO](../vsto/programming-vsto-add-ins.md)   
 [Tworzenie rozwiązań pakietu Office](../vsto/developing-office-solutions.md)   
 [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)   
 [Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md)  
  
  