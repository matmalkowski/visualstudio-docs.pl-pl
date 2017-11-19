---
title: "Tworzenie folderów kontenera nadrzędnego dla rozwiązań | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- solutions, creating parent containers
- source control plug-ins, creating parent containers
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6ea901fe4e380fd867db1c63e44bc1cb6e144feb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="creating-parent-container-folders-for-solutions"></a>Tworzenie folderów kontenera nadrzędnego dla rozwiązania
Źródłowy formant wtyczek interfejsu API w wersji 1.2 użytkownik może określić lokalizację docelową kontroli źródła z jednym elementem głównym dla wszystkich projektów sieci Web w ramach rozwiązania. To z jednym elementem głównym jest nazywany skanowania Super Unified głównego (SUR).  
  
 Źródło kontroli wtyczek interfejsu API w wersji 1.1 Jeśli użytkownik dodany zakresu rozwiązanie do kontroli źródła, użytkownik został monit o określenie jedno miejsce docelowe kontroli źródła dla każdego projektu sieci Web.  
  
## <a name="new-capability-flags"></a>Nowe możliwości flagi  
 `SCC_CAP_CREATESUBPROJECT`  
  
 `SCC_CAP_GETPARENTPROJECT`  
  
## <a name="new-functions"></a>Nowe funkcje  
 [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)  
  
 [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE prawie zawsze tworzy SUR folder podczas dodawania rozwiązanie do kontroli źródła. W szczególności robi to w następujących przypadkach:  
  
-   Projekt jest udział plików projektu sieci Web.  
  
-   Istnieją różne dyski dla projektu i pliku rozwiązania.  
  
-   Istnieją różne akcje dla projektu i pliku rozwiązania.  
  
-   Projekty zostały dodane oddzielnie (w rozwiązaniu do kontroli źródła).  
  
 W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zaleca się, że nazwa folderu SUR być taka sama jak nazwa rozwiązania bez rozszerzenia. W poniższej tabeli przedstawiono zachowania w dwóch wersjach.  
  
|Funkcja|tSource kontroli wtyczek interfejsu API w wersji 1.1|Wtyczka interfejsu API w wersji 1.2 kontroli źródła|  
|-------------|----------------------------------------------|---------------------------------------------|  
|Dodaj rozwiązanie do SCC|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccGetProjPath()<br /><br /> SccOpenProject()|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccCreateSubProject()<br /><br /> SccCreateSubProject()<br /><br /> SccOpenProject()|  
|Dodaj projekt do rozwiązania pod kontrolą źródła|SccGetProjPath()<br /><br /> OpenProject()|SccGetParentProjectPath()<br /><br /> SccOpenProject() **Uwaga:** Visual Studio zakłada, że rozwiązanie jest bezpośrednim elementem podrzędnym elementu SUR.|  
  
## <a name="examples"></a>Przykłady  
 W poniższej tabeli przedstawiono dwa przykłady. W obu przypadkach [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] użytkownik otrzyma monit o lokalizację docelową dla rozwiązania pod kontrolą źródła dopóki *user_choice* jest określony jako miejsca docelowego. W przypadku user_choice rozwiązania i dwa projekty zostaną dodane bez monitowania użytkownika o lokalizacji docelowych kontroli źródła.  
  
|Rozwiązanie zawiera|W lokalizacji dysku|Struktura domyślnej bazy danych|  
|-----------------------|-----------------------|--------------------------------|  
|sln1.sln<br /><br /> Serwera Web1<br /><br /> Sieci Web 2|C:\Solutions\sln1<br /><br /> C:\Inetpub\wwwroot\Web1<br /><br /> \\\server\wwwroot$\web2|$/*user_choice*/sln1<br /><br /> $/*user_choice*  /C/serwera Web1<br /><br /> $/*user_choice*/Web2|  
|sln1.sln<br /><br /> Serwera Web1<br /><br /> Win1|C:\Solutions\sln1<br /><br /> D:\Inetpub\wwwroot\Web1<br /><br /> C:\solutions\sln1\Win1|$/*user_choice*/sln1<br /><br /> $/*user_choice*  /D/serwera web1<br /><br /> $/*user_choice*  /sln1/win1|  
  
 SUR folderze i jego podfolderach są tworzone niezależnie od tego, czy operacja została anulowana lub kończy się niepowodzeniem z powodu błędu. Ich nie są automatycznie usuwane w warunkach Anuluj lub błędu.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ustawienia domyślne zachowanie w wersji 1.1, jeśli wtyczka do kontroli źródła nie może zwracać `SCC_CAP_CREATESUBPROJECT` i `SCC_CAP_GETPARENTPROJECT` flagi możliwości. Ponadto użytkownicy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] można wybrać powrócić do zachowania w wersji 1.1, ustawiając wartość następującego klucza DWORD: 00000001:  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl" = dword: 00000001  
  
## <a name="see-also"></a>Zobacz też  
 [Nowości w źródła formantu wtyczka interfejsu API wersji 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)