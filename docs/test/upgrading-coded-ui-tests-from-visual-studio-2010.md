---
title: "Uaktualnianie kodowanych testów interfejsu użytkownika z Visual Studio 2010 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11232a83-73ea-46bd-bc0c-46f74f6e3a42
caps.latest.revision: "33"
ms.author: douge
manager: douge
ms.openlocfilehash: 8b854bcfcb7227a454023f89ce732706b1e545cc
ms.sourcegitcommit: c0422a3d594ea5ae8fc03f1aee684b04f417522e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2017
---
# <a name="upgrading-coded-ui-tests-from-visual-studio-2010"></a>Aktualizowanie kodowanych testów interfejsu użytkownika z Visual Studio 2010
Testowanie projektów zawierających kodowane testy interfejsu użytkownika, które zostały utworzone w [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] SP1 dyskretnie naprawy po otwarciu w programie Visual Studio 2012 lub nowszym. Projekty testowe zaznaczenie do kontroli źródła plików projektu są wyewidencjonowane dla tej naprawy. Po naprawieniu te testowanie projektów zawierających kodowane może testy interfejsu użytkownika, a następnie można użyć zarówno [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] z dodatkiem SP1 i [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)].  
  
 **Wymagania**  
  
-   Visual Studio Enterprise  
  
> [!NOTE]
>  Visual Studio zawiera więcej niż jeden typ projektu testowego. Jeśli tworzysz nowy kodowanego testu interfejsu użytkownika, zostanie on utworzony typ projektu testowego kodowanego interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [uaktualniania testów z wcześniejszych wersji programu Visual Studio](http://msdn.microsoft.com/en-us/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52).  
  
> [!WARNING]
>  [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)]Projekty testowe, które zawierają kodowane testy interfejsu użytkownika musi zostać również przebudowany po otwarciu projektu testu w [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] lub [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] side-by-side z [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)].  
  
> [!WARNING]
>  Jeśli projekt testowy, który został utworzony w [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] i zawiera tylko testy jednostkowe jest otwarty w [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], kodowanych testów interfejsu użytkownika nie można dodać do niego. Podobnie, nie można dodać kodowanego testu interfejsu użytkownika do jednostkowy projekt testowy, który został utworzony w [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)].  
  
## <a name="compatibility-issues-between-visual-studio-2010-and-visual-studio-2012-or-later"></a>Problemy ze zgodnością między programu Visual Studio 2010 i Visual Studio 2012 lub nowszy  
 Poniższa tabela zawiera listę problemów pod uwagę podczas migracji kodowanych testów interfejsu użytkownika między [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] i [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)].  
  
> [!CAUTION]
>  Jest to znany problem dotyczący odwołań w kodowanego interfejsu użytkownika projekty testowe nie są widoczne w Eksploratorze rozwiązań. Aby uzyskać więcej informacji, zobacz plik ReadMe włączone [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] nośnika instalacyjnego.  
  
|Kodowane funkcji interfejsu użytkownika|Problem|Rozwiązanie|  
|----------------------------|-----------|--------------|  
|Testowanie interfejsu użytkownika programu Silverlight nie jest obsługiwany w[!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]|**Kompilacja zakończy się niepowodzeniem.**<br /><br /> Jeśli masz [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] funkcja dodatkiem Service Pack 2 i ma utworzyć kodowany projektów testów interfejsu użytkownika dla aplikacji Silverlight, te projekty nie można otworzyć w [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)].|Zaleca się zarządzanie te projekty w [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] tylko funkcja dodatkiem Service Pack 2.|  
|Testowanie interfejsu użytkownika Firefox nie jest obsługiwany w[!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]|**Kompilacja zostanie wykonana pomyślnie, nie powiedzie się uruchomienie testu**<br /><br /> Jeśli masz [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] funkcja dodatkiem Service Pack 2 i zostały utworzone kodowanego projektów testów interfejsu użytkownika dla aplikacji sieci web w programie Firefox, te projekty nie można otworzyć w [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)].|Zaleca się zarządzanie te projekty w [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] tylko funkcja dodatkiem Service Pack 2.|  
|Nowy kod interfejsu użytkownika testowania interfejsów API zostały dodane w[!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]|**Kompilacja zakończy się niepowodzeniem.**<br /><br /> Jeśli utworzysz kodowanych testów interfejsu użytkownika przy użyciu nowego interfejsu użytkownika testowania interfejsu API w [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], nie można otworzyć te projekty w [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)].|Przy użyciu interfejsu API nowe projekty powinny być zarządzane w [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] tylko.|  
|W [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)], odwołania zostały dodane wewnątrz instrukcji 'Wybierz' w pliku csproj. W [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], jest używany plik celów opinie do zawierają odwołania kodowanego interfejsu użytkownika zestawu testowego.|W [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], kodowanego testu interfejsu użytkownika nie można dodać do projektu testowego utworzone w [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] (lub z dodatkiem SP1) nie zawiera kodowanego testu interfejsu użytkownika.<br /><br /> Proces naprawy dodaje plik elementów docelowych i wybierz instrukcji. Jeśli kodowanego testu interfejsu użytkownika nie jest w projekcie testowym projektu jest oznaczony jako naprawić i odpowiednie odwołania nie zostaną dodane przy dodawaniu kodowanego testu interfejsu użytkownika w [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)].|Musisz utworzyć nowy projekt testowy za pomocą tego samego rozwiązania [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] i dodać nowe kodowanego testu interfejsu użytkownika. Alternatywnie kodowanych testów interfejsu użytkownika można dodać do projektu testu w [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] z dodatkiem SP1 i otworzyć projekt który w [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)].|  
  
##  <a name="UpgradingCodedUIFromVS2010_Update"></a>Visual Studio 2010 z dodatkiem SP1 Update  
 Aktualizacja [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] z dodatkiem SP1 i obsługa zgodności dla programu Visual Studio 2012 lub nowszego i systemu Windows 8 lub nowszy, jest dostępny do pobrania na [Microsoft Download Center](http://www.microsoft.com/download/details.aspx?id=34677) i zaktualizuj również co program Visual Studio.  
  
 Po zainstalowaniu aktualizacji, następujące [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] zwiększona funkcji narzędzia w kodowanego testu interfejsu użytkownika dla systemu Windows 8 z dodatkiem SP1:  
  
-   Kodowany Test interfejsu użytkownika dla kontrolki oparte na programie .NET Framework 4.5 Windows Presentation Foundation (WPF) firmy Microsoft można uruchomić na komputerze z systemem Windows 8.  
  
-   Na komputerze z systemem Windows 8, można uruchomić testu kodowanego interfejsu użytkownika dla programu Internet Explorer 10 64-bitowej (x 64).  
  
 Aktualizacja zawiera również rozwiązania następujących problemów:  
  
-   **Pokrycie kodu:** brakiem można otworzyć pliku pokrycia kodu (.coverage), który jest tworzony przez program Visual Studio 2012 w [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] z dodatkiem SP1.  
  
-   **Skrętki artefakty testu:** Twojego zespołu ma artefaktów testu, który jest przypisany do nieprawidłowego użytkownika w Team Foundation Server (TFS) 2010. Na przykład użytkownik odejścia z firmy, ale nadal ma przypisane do niego przypadek testowy. TFS 2010 można uaktualnić do programu TFS 2012. Możesz użyć [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] 2010 do nawiązania połączenia uaktualnionym serwerze TFS. Nie jest możliwe do przypisania artefaktów testu wszyscy użytkownicy TFS przy użyciu [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] 2010.  
  
-   **Testy obciążenia:** po uruchomieniu testu obciążenia wraz z typem sieci innych niż profil sieci lokalnej (LAN) na komputerze, to systemem Windows 8, sterownik emulatora sieci powoduje awarię systemu operacyjnego. Aby uzyskać więcej informacji, zobacz [2736182 artykułu KB](http://support.microsoft.com/kb/2736182).  
  
## <a name="see-also"></a>Zobacz też  
 [Przenoszenie, migrowanie i uaktualnianie projektów programu Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md)   
 [Aktualizowanie testów z wcześniejszych wersji programu Visual Studio](http://msdn.microsoft.com/en-us/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52)   
 [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)   
 [Generowanie kodowanego testu interfejsu użytkownika na podstawie dotychczasowego rejestrowania akcji](/devops-test-docs/test/generating-a-coded-ui-test-from-an-existing-action-recording)   
 [Obsługiwane konfiguracje oraz platformy zakodowanych testów interfejsu użytkownika i nagrywania akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
