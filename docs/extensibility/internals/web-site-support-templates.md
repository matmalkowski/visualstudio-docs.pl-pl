---
title: Szablony witryn sieci Web pomocy technicznej | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: we site projects, templates
ms.assetid: 37173c97-486b-4b3c-8ed3-cf5890c4de23
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c4e3d64f77064c04e131853786495c921711f2d0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="web-site-support-templates"></a>Szablony witryn sieci Web pomocy technicznej
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Witryny sieci Web szablonów projektów i elementów podać zastępcze projektu i elementu wielokrotnego użytku i dostosowywanych witryny sieci Web, które przyspieszyć ten proces programowania, usuwając konieczność tworzenia nowej witryny sieci Web projektów i elementów od początku. Aby uzyskać więcej informacji na temat [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] szablony, zobacz [szablony tworzenie projektów i elementów](../../ide/creating-project-and-item-templates.md).  
  
## <a name="project-template-folder"></a>Folder szablonu projektu  
 Szablony szablonu projektu sieci Web są instalowane w [*ścieżki instalacji usługi Visual Studio*] \Common7\IDE\ProjectTemplates\Web\\, każdy w podfolderze o nazwie po web język programowania.  
  
## <a name="project-file"></a>Plik projektu  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Zintegrowane środowisko programistyczne (IDE) wymaga rozszerzenia pliku projektu jako mapują szablonu do typu właściwy projekt. .Webproj rozszerzenie pliku zastępczego projektu, ponieważ projekty sieci Web nie ma pliku projektu, jest zarejestrowany w tym.  
  
 Opcjonalnie można dodać do szablonu, aby włączyć system projektu sieci Web ustawić język domyślny, w ciągu nazwy języka **Dodaj nowy element** okno dialogowe dla elementów na podstawie szablonu. Ciąg musi być pierwszym wierszem pliku i musi odpowiadać zarówno nazwę zarejestrowany pod AddItemLanguageName w rejestracja w aparacie Intellisense, jak i nazwę zarejestrowanego w Subtype(VsTemplate) projektu. Aby uzyskać więcej informacji, zobacz [witryny sieci Web pomocy technicznej atrybutów](../../extensibility/internals/web-site-support-attributes.md).  
  
 Jeśli ciąg nie jest obecny, system projektu sieci Web będzie podejmować próby ustalenia na podstawie rozszerzeń atrybutu i plik języka strony dodane do projektu sieci Web przez szablon projektu szablon domyślny język.  
  
## <a name="project-templates"></a>Szablony projektu  
 Szablony projektów witryny sieci Web są używane do tworzenia nowych witryn sieci Web w odpowiedzi na **nowej witryny sieci Web** na **pliku** menu. Obecnie obsługiwane są trzy typy projektu witryny sieci Web:  
  
-   Pusta witryna sieci Web  
  
-   Witryna sieci Web  
  
-   Projekty usługi sieci Web  
  
### <a name="empty-web-site-projects"></a>Pusta witryna sieci Web  
 Te pliki utworzyć kopię zapasową witryny sieci Web w odpowiedzi na **pusta witryna sieci Web** polecenia, które jest dostępne po wskazaniu **nowej witryny sieci Web** na **pliku** menu:  
  
-   EmptyWeb.vstemplate  
  
     Plik szablonu, który przeprowadzi tworzenie nowych pusta witryna sieci Web.  
  
-   EmptyWeb.webproj  
  
     Ten plik jest artefaktu systemu szablonu projektu. Spełnia on odwołanie do pliku projektu w pliku EmptyWeb.vstemplate.  
  
### <a name="web-site-projects"></a>Witryna sieci Web  
 Te pliki, Utwórz nową witrynę sieci Web w odpowiedzi na **witryny sieci Web ASP.NET** polecenia, które jest dostępne po wskazaniu **nowej witryny sieci Web** na **pliku** menu:  
  
-   Default.aspx  
  
     Domyślną stronę główną dla nowej witryny sieci Web. Atrybut Language określa język plik codebehind i atrybut CodeFile określa zależny plik zawierający kod został skojarzony z tą stroną.  
  
-   Default.aspx. *rozszerzenia*  
  
     Plik zależny, który zawiera kod został domyślną stronę główną. Określa język plik codebehind *rozszerzenia* tego pliku.  
  
-   plik Web.config  
  
     Główny plik konfiguracyjny web.site.  
  
-   WebApplication.vstemplate  
  
     Plik szablonu, który określa zawartość rozwiązania witryny sieci Web i wymuszenie utworzenia w folderze App_Data.  
  
-   WebApplication.webproj  
  
     Ten plik jest artefaktu systemu szablonu projektu. Spełnia on odwołanie do pliku projektu w pliku WebApplication.vstemplate.  
  
### <a name="web-service-projects"></a>Projekty usługi sieci Web  
 Te pliki, Utwórz nową witrynę sieci Web w odpowiedzi na **usługi sieci Web ASP.NET** polecenia, która jest dostępna po wskazaniu **nowej witryny sieci Web** na **pliku** menu:  
  
-   Service.asmx  
  
     Strona HTML nową usługę sieci Web. Atrybut Language określa język został, a atrybut plik CodeBehind określa zależnych plik zawierający kod został skojarzony z tą usługą.  
  
-   Usługa. *rozszerzenia*  
  
     Plik zależny implementuje klasy usługi. Określa język plik codebehind *rozszerzenia* tego pliku.  
  
-   plik Web.config  
  
-   Główny plik konfiguracyjny web.site.  
  
-   WebService.vstemplate  
  
     Plik szablonu, który określa zawartość rozwiązania witryny sieci Web i wymuszenie utworzenia folderów App_Data i App_Code. Usługa. *rozszerzenia* plik jest kopiowany do folderu App_Code.  
  
-   WebService.webproj  
  
     Ten plik jest artefaktu systemu szablonu projektu. Spełnia on odwołanie do pliku projektu w pliku WebService.vstemplate.  
  
## <a name="project-item-template-folder"></a>Folder szablonu elementu projektu  
 Szablony szablonu elementu projektu sieci Web są instalowane w [*ścieżki instalacji usługi Visual Studio*] \Common7\IDE\ItemTemplates\Web\\, każdy w podfolderze o nazwie po jej sieć web języka programowania.  
  
## <a name="project-item-templates"></a>Szablony elementów projektu  
 Szablony elementów projektu witryny sieci Web są używane do dodawania nowych stron sieci Web do witryny sieci Web w odpowiedzi na **Dodaj istniejący element** polecenia. Tego rodzaju stron sieci Web są obecnie obsługiwane:  
  
-   Nowa klasa  
  
-   Strony HTML  
  
-   Nowy formularz sieci Web  
  
-   Nowej strony wzorcowej  
  
### <a name="new-class"></a>Nowa klasa  
 Ten szablon tworzy nowy plik źródłowy, który definiuje pustą klasę w odpowiedzi na **Dodaj nową klasę** polecenia.  
  
-   Klasa. *rozszerzenia*  
  
     Plik źródłowy, który implementuje pustą klasę. Określa język plik codebehind *rozszerzenia* tego pliku.  
  
-   Class.vstemplate  
  
     Plik szablonu tworzy plik źródłowy, który określa jego zawartość.  
  
### <a name="new-html-page"></a>Strony HTML  
 Ten szablon tworzy nową stronę sieci Web w odpowiedzi na **Dodaj nową stronę HTML** polecenia.  
  
-   HTMLPage.htm  
  
     Początkowy zawartości strony sieci Web. Ta strona sieci Web zwykle nie ma skojarzony plik codebehind zależnych pliku. Aby utworzyć stronę inteligentne z pliku został skojarzony, należy użyć szablonu formularza sieci Web.  
  
-   HTMLPage.vstemplate  
  
     Plik szablonu, który tworzy stronę sieci Web i określa jego zawartość.  
  
### <a name="new-webform"></a>Nowy formularz sieci Web  
 Ten szablon tworzy nową stronę sieci Web inteligentne w odpowiedzi na **Dodaj nowy formularz sieci Web** polecenia.  
  
 Aby utworzyć plik źródłowy został zależnych, wybierz **umieść kod w osobnym pliku**. W przeciwnym razie pojedyncza strona sieci Web zostanie utworzone pusty blok skryptów i nie \<% strony % > dyrektywy dołączenie pliku zależnego.  
  
 Aby utworzyć strony zawartości dla wybranej strony wzorcowej, wybierz **wybierz strony wzorcowej**.  
  
-   WebForm.aspx  
  
     Początkowy zawartości strony sieci Web. Ta strona sieci Web nie ma skojarzony plik codebehind zależnych pliku.  
  
-   WebForm_cb.aspx  
  
     Początkowy zawartości strony sieci Web. Ta strona sieci Web ma został skojarzony plik zależnych.  
  
-   Plik CodeBehind. *rozszerzenia*  
  
     Plik zależny implementuje klasy formularza sieci Web. Określa język plik codebehind *rozszerzenia* tego pliku.  
  
-   ContentPage.aspx  
  
     Początkowy zawartości strony sieci Web jako zawartości strony. Ta strona sieci Web nie ma skojarzony plik codebehind zależnych pliku.  
  
-   ContentPage_cb.aspx  
  
     Początkowy zawartości strony sieci Web jako zawartości strony. Ta strona sieci Web ma został skojarzony plik zależnych.  
  
-   WebForm.vstemplate  
  
     Plik szablonu określająca zawartość nowej strony sieci web i jego plików zależnych, jeśli istnieje.  
  
### <a name="new-master-page"></a>Nowa strona wzorcowa  
 Ten szablon tworzy nową stronę wzorcową w odpowiedzi na **Dodaj nową stronę wzorcową** polecenia.  
  
 Aby utworzyć plik źródłowy został zależnych, wybierz **umieść kod w osobnym pliku**. W przeciwnym razie pojedyncza strona sieci Web zostanie utworzone pusty blok skryptów i nie \<% strony % > dyrektywy dołączenie pliku zależnego.  
  
-   MasterPage.master  
  
     Początkowy zawartości strony wzorcowej. Ta strona wzorcowa nie ma skojarzony plik codebehind zależnych pliku.  
  
-   MasterPage_cb.master  
  
     Początkowy zawartości strony wzorcowej. Strona wzorcowa ma skojarzony plik codebehind plików zależnych.  
  
-   Plik CodeBehind. *rozszerzenia*  
  
     Plik zależny implementuje klasy strony wzorcowej. Określa język plik codebehind *rozszerzenia* tego pliku.  
  
-   MasterPage.vstemplate  
  
     Plik szablonu określająca zawartość nowej strony wzorcowej i jego plików zależnych, jeśli istnieje.  
  
## <a name="see-also"></a>Zobacz też  
 [Witryna sieci Web pomocy technicznej](../../extensibility/internals/web-site-support.md)