---
title: Zabezpieczanie rozwiązań pakietu Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, security
- Office applications [Office development in Visual Studio], security
- security [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: dd86b7c15fa198b37ce15c75b13d2863f56ca3ba
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34693373"
---
# <a name="secure-office-solutions"></a>Zabezpieczanie rozwiązań pakietu Office
  Model zabezpieczeń dla rozwiązań pakietu Office obejmuje kilka technologii: [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)], Centrum zaufania Microsoft Office i strefy witryn z ograniczeniami programu Internet Explorer. W poniższych sekcjach opisano, jak działają funkcje zabezpieczeń:  
  
-   [Udziel zaufania do rozwiązań pakietu Office](#GrantingTrustToSolutions)  
  
-   [Udziel zaufania do dokumentów](#GrantingTrustToDocuments)  
  
-   [Udziel zaufania, używając Instalatora Windows](#GrantingTrustWindowsInstaller)  
  
-   [Zagadnienia dotyczące zabezpieczeń określone dla rozwiązań pakietu Office](#Security)  
  
-   [Zabezpieczenia w czasie projektowania](#SecurityDuringDeployment)  
  
-   [Visual Studio Tools dla pakietu Office runtime](#VisualStudioToolsForOfficeRuntime)  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
##  <a name="GrantingTrustToSolutions"></a> Udziel zaufania do rozwiązań pakietu Office  
 Udzielanie zaufania do rozwiązań pakietu Office oznacza modyfikowanie zasad zabezpieczeń dla każdego użytkownika końcowego zaufania rozwiązania pakietu Office, w oparciu o następujące dowody:  
  
-   Certyfikat używany do podpisywania manifestu wdrożenia.  
  
-   Adres URL w manifeście wdrażania.  
  
 Aby uzyskać więcej informacji, zobacz [przyznać zaufania do rozwiązań pakietu Office](../vsto/granting-trust-to-office-solutions.md).  
  
##  <a name="GrantingTrustToDocuments"></a> Udziel zaufania do dokumentów  
 Dostosowywanie poziomie dokumentu wymaga dokumentu w katalogu, który jest oznaczony jako zaufanej lokalizacji. Aby uzyskać więcej informacji, zobacz [przyznać zaufania do dokumentów](../vsto/granting-trust-to-documents.md).  
  
##  <a name="GrantingTrustWindowsInstaller"></a> Udziel zaufania, używając Instalatora Windows  
 Instalator systemu Windows można użyć do utworzenia pliku MSI, aby zainstalować rozwiązań pakietu Office do katalogu Program Files wymaga uprawnień administratora. Dla rozwiązań pakietu Office w katalogu Program Files Visual Studio 2010 Tools dla pakietu Office runtime uwzględnia tych rozwiązań pakietu Office jako zaufane i nie jest wyświetlany monit zaufania ClickOnce.  
  
##  <a name="Security"></a> Zagadnienia dotyczące zabezpieczeń określone dla rozwiązań pakietu Office  
 Funkcji zabezpieczeń zapewnianych przez [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], i Microsoft Office może pomóc w ochronie przed różnymi potencjalne zagrożenia w rozwiązaniach pakietu Office. Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące zabezpieczeń określone dla rozwiązań pakietu Office](../vsto/specific-security-considerations-for-office-solutions.md).  
  
##  <a name="SecurityDuringDeployment"></a> Zabezpieczenia w czasie projektowania  
 Aby ułatwić procesie tworzenia aplikacji programu Visual Studio ustawia zasady zabezpieczeń, które jest wymagane do uruchomienia i debugowanie rozwiązania na komputerze zawsze w przypadku kompilowania projektu. W niektórych scenariuszach może być konieczne dodatkowe zabezpieczenia czynności Tworzenie projektu.  
  
### <a name="document-level-solutions"></a>Rozwiązania na poziomie dokumentu  
 Pełną ścieżkę dokumentu muszą być dodane do listy zaufanych lokalizacji w aplikacji pakietu Microsoft Office, jeśli tworzysz następujących typów projektów:  
  
-   Poziome dokumentu rozwiązań, które są w sieciowym udziale plików, takich jak  *\\\servername\sharename*.  
  
-   Poziome dokumentu rozwiązania dla programu Word, używanego *doc* lub *docm* plików.  
  
 Obejmują podkatalogów, Dodaj lokalizację dokumentu do listy zaufanych lokalizacji lub w szczególności obejmują debugowania i kompilowania folderów. Aby uzyskać więcej informacji, zobacz artykuł Microsoft Office Online Pomoc [Utwórz, usuń lub zmień zaufanej lokalizacji plików](https://support.office.com/en-au/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).  
  
### <a name="temporary-certificates"></a>Certyfikaty tymczasowe  
 Visual Studio tworzy certyfikat tymczasowe, jeśli certyfikat podpisywania nie istnieje. Należy użyć tego certyfikatu tymczasowe tylko podczas programowania i zakupu oficjalnego certyfikatu do wdrożenia.  
  
 Tymczasowy certyfikat jest generowany po pierwszym utworzeniu projektu pakietu Office. Przy następnym naciśnięciu **F5**, projekt zostanie skompilowany ponownie, ponieważ projekt jest oznaczony jako zmieniony po dodaniu certyfikatu.  
  
 Może istnieć wiele certyfikatów tymczasowych po chwili, więc należy wyczyścić certyfikatów tymczasowych co pewien czas.  
  
##  <a name="VisualStudioToolsForOfficeRuntime"></a> Visual Studio Tools dla pakietu Office runtime  
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Zawiera funkcje, aby sprawdzić tożsamość wydawcy i uprawnień, które są przypisywane do dostosowania. Sprawdzi te uprawnienia za pomocą sekwencji kontroli zabezpieczeń.  
  
### <a name="security-during-customization-loading"></a>Zabezpieczenia w trakcie dostosowywania realizowanego ładowania  
 Po załadowaniu dostosowania poziomie dokumentu [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] zawsze sprawdzają, czy dokument znajduje się na liście zaufanych lokalizacji. Ponadto środowisko uruchomieniowe sprawdza, czy rozwiązanie żądań FullTrust w manifeście aplikacji. Wykonuje dodatkowe zabezpieczenia nie są sprawdzane podczas ładowania dostosowań.  
  
### <a name="sequence-of-security-checks-during-installation"></a>Sekwencja kontroli zabezpieczeń podczas instalacji  
 Po zainstalowaniu lub zaktualizowaniu, rozwiązania do pakietu Office [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] wykonuje zestawu testów zabezpieczeń w określonej kolejności do podjęcia decyzji o zaufaniu. Rozwiązanie jest zainstalowane lub zaktualizować tylko wtedy, gdy środowisko uruchomieniowe Określa, że rozwiązanie jest zaufany.  
  
 Proces instalacji można uruchomić w jednym z czterech sposobów: przez uruchomienie programu instalacyjnego, otwierając manifest wdrażania, otwierając hosta aplikacji Microsoft Office lub uruchamiając *VSTOInstaller.exe*.  
  
 Pierwszy kontrola zabezpieczeń dotyczy tylko rozwiązania na poziomie dokumentu. Dokument rozwiązanie na poziomie dokumentu musi być w zaufanej lokalizacji. Jeśli dokument jest w udziale plików sieci zdalnej lub ma *doc* lub *docm* rozszerzenia nazwy pliku lokalizacji tego dokumentu musi zostać dodany do listy zaufanych lokalizacji. Aby uzyskać więcej informacji, zobacz [przyznać zaufania do dokumentów](../vsto/granting-trust-to-documents.md).  
  
 ![Zabezpieczenia programu VSTO — instalowanie z Microsoft Office](../vsto/media/host-install.png "zabezpieczeń VSTO — instalowanie z Microsoft Office")  
  
 Następny zestaw kontroli zabezpieczeń są z [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] i ClickOnce. Przeszły, rozwiązań pakietu Office muszą zażądać uprawnień FullTrust, podpisanie certyfikatu, który nie znajduje się na liście niezaufanych wydawcy i znajdować się w lokalizacji, która nie znajduje się w strefie Internet Explorer z ograniczeniami. Jeśli certyfikat znajduje się na liście zaufanego wydawcy, rozwiązanie jest instalowana natychmiast. W przeciwnym razie nie awaria jednej kontroli, rozwiązanie będzie nadal do ostatniej kontroli.  
  
 ![Zabezpieczenia programu VSTO dotyczące instalowania rozwiązań](../vsto/media/installing.png "VSTO zabezpieczeń dotyczące instalowania rozwiązań")  
  
 Jeśli [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] zaufania wiersza jest dozwolone i rozwiązanie nie ma jeszcze udzielonego zaufania i środowiska uruchomieniowego zezwala decyzja dotycząca zaufania ma zostać wykonane przez użytkownika końcowego. Jeśli użytkownik przyznaje zaufania do rozwiązania, wpis jest dodawany do listy dołączania użytkowników. Wszystkie rozwiązania na liście dołączania użytkowników mają pełnego zaufania i można instalować i uruchom.  
  
 Począwszy od programu Visual Studio 2010, lista dołączania jest pomijane, jeśli rozwiązań pakietu Office został zainstalowany przy użyciu Instalatora Windows (MSI) do katalogu Program Files. Aby uzyskać więcej informacji, zobacz [zaufania rozwiązań pakietu Office przy użyciu list dołączania](../vsto/trusting-office-solutions-by-using-inclusion-lists.md).  
  
 ![Zabezpieczenia programu VSTO — przy użyciu Instalatora, aby zainstalować](../vsto/media/setup-vstoinstaller.png "zabezpieczeń VSTO — przy użyciu Instalatora, aby zainstalować")  
  
## <a name="see-also"></a>Zobacz także  
 [Udziel zaufania do rozwiązań pakietu Office](../vsto/granting-trust-to-office-solutions.md)   
 [Udziel zaufania do dokumentów](../vsto/granting-trust-to-documents.md)   
 [Zaufania rozwiązań pakietu Office przy użyciu list dołączania](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)   
 [Porady: Konfigurowanie zabezpieczeń listy dołączania](../vsto/how-to-configure-inclusion-list-security.md)   
 [Porady: podpisywanie rozwiązań pakietu Office](../vsto/how-to-sign-office-solutions.md)   
 [Rozwiązywanie problemów z zabezpieczeniami rozwiązań pakietu Office](../vsto/troubleshooting-office-solution-security.md)   
 [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce — odwołanie](/visualstudio/deployment/clickonce-reference)   
 [Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md)  
  
  