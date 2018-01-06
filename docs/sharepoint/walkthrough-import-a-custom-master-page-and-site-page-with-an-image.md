---
title: "Wskazówki: Importowanie niestandardowej strony wzorcowej oraz strony witryny z obrazem | Dokumentacja firmy Microsoft"
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
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
ms.assetid: d1703957-81e2-47e1-b4ca-6a8d550d8da2
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: ef55a90b55314bf7ab2c5aa6259f09b62a350da3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-import-a-custom-master-page-and-site-page-with-an-image"></a>Wskazówki: importowanie niestandardowej strony wzorcowej oraz strony witryny z obrazem
  W tym przewodniku pokazano, jak zaimportować SharePoint niestandardowej strony wzorcowej oraz strony witryny, która ma obrazu na [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektu programu SharePoint.  
  
 W tym przewodniku przedstawiono sposób wykonania następujących zadań:  
  
-   Tworzenie niestandardowej strony wzorcowej oraz strony witryny przy użyciu obrazu w programie SharePoint Designer.  
  
-   Wyeksportuj niestandardowej strony wzorcowej, obraz oraz strony witryny do pliku rozwiązania (wsp) programu SharePoint.  
  
-   Importowanie i wdrażanie w pliku wsp [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektu programu SharePoint przy użyciu projektu Importowanie pakietu rozwiązań programu SharePoint.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Musi mieć następujące składniki w tym przewodniku:  
  
-   Obsługiwane wersje programu [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] i programu SharePoint. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][Wymagania związane z opracowywaniem rozwiązań SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Program Visual Studio.  
  
-   SharePoint Designer 2010.  
  
## <a name="create-items-in-sharepoint-designer"></a>Tworzenie elementów w programie SharePoint Designer  
 W tym przykładzie pokazano, jak utworzyć trzy elementy w programie SharePoint Designer eksportu: niestandardowej strony wzorcowej, witryna, który odwołuje się do niestandardowej strony wzorcowej i plikiem obrazu na stronie witryny. Obraz jest dodawany do folderu /images/ w programie SharePoint.  
  
#### <a name="to-create-a-custom-master-page-in-sharepoint-designer"></a>Aby utworzyć niestandardowe strony głównej w programie SharePoint Designer  
  
1.  W programie SharePoint Designer w okienku nawigacji wybierz **stron wzorcowych** obiektu lokacji.  
  
2.  Na **stron wzorcowych** wstążki, wybierz **puste strony wzorcowej**.  
  
3.  Wybierz nowej strony wzorcowej, a następnie na **stron wzorcowych** wstążki, wybierz **Edytuj plik**.  
  
4.  W dolnej części programu SharePoint Designer, wybierz **kod** kartę.  
  
5.  Zastąp istniejący kod znaczników następujący kod znaczników.  
  
    ```  
    <%@ Master Language="C#" %>  
    <%@ Register tagprefix="SharePoint" namespace="Microsoft.SharePoint.WebControls" assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>  
    <html dir="ltr">  
    <head runat="server">  
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8">  
    <SharePoint:RobotsMetaTag runat="server" __designer:Preview="" __designer:Values="<P N='InDesign' T='False' /><P N='ID' T='ctl00' /><P N='Page' ID='1' /><P N='TemplateControl' ID='2' /><P N='AppRelativeTemplateSourceDirectory' R='-1' />"></SharePoint:RobotsMetaTag>  
    <title>Web Page</title>  
    </head>  
    <body>  
    <form id="form1" runat="server">  
    <asp:ContentPlaceHolder id="ContentPlaceHolderMain"   
            runat="server">  
          </asp:ContentPlaceHolder>  
    </form>  
    </body>  
    </html>  
    ```  
  
6.  Wybierz pozycję Zapisz stronę **stron wzorcowych** , a następnie zmień nazwę strony wzorcowej jako **mybasic1.master**.  
  
## <a name="add-an-image-to-the-content-database-in-sharepoint-designer"></a>Dodawanie obrazu do bazy danych zawartości w programie SharePoint Designer  
 Teraz możesz dodać obraz do wyświetlania na stronie witryny. Baza danych zawartości programu SharePoint jest wdrażany.  
  
#### <a name="to-add-an-image-to-the-content-database-in-sharepoint-designer"></a>Aby dodać obraz do bazy danych zawartości w programie SharePoint Designer  
  
1.  W okienku nawigacji wybierz **wszystkie pliki** lokacji obiektu, a następnie, w widoku drzewa wybierz **obrazów** folderu.  
  
2.  Na **wszystkie pliki** wstążki, wybierz **plików importu**, wybierz plik, a następnie wybierz **OK** przycisku. W tym przykładzie plik o nazwie **myimg1.png**.  
  
     Opcjonalnie możesz utworzyć podfolder, aby ułatwić organizowanie obrazów.  
  
3.  Zamknij **importu** okno dialogowe.  
  
## <a name="create-a-site-page"></a>Tworzenie strony witryny  
 Ta strona podstawowa lokacji używa niestandardowej strony wzorcowej i wyświetla obraz, który został dodany w poprzednim kroku.  
  
#### <a name="to-create-a-site-page"></a>Aby utworzyć stronę lokacji  
  
1.  W okienku nawigacji wybierz **stron w witrynie** obiektu.  
  
2.  Na **stron** wstążki, wybierz **strony** przycisku, wybierz **ASPX** strony typu, a następnie podaj nazwę nowego pliku **mycontentpage1.aspx**.  
  
     Opcjonalnie możesz utworzyć podfolder, aby ułatwić organizowanie stron witryny.  
  
3.  Na liście stron witryny wybierz **MyContentPage1.aspx** otwórz jego stronę właściwości, a następnie w dolnej części strony, należy wybrać **edycji pliku** łącza.  
  
     Jeśli komunikat jest wyświetlany mówi, że ta strona nie zawiera żadnych obszarów, które można edytować w trybie awaryjnym i zapyta, czy chcesz otworzyć tę stronę w trybie zaawansowanym, wybierz **tak** przycisku.  
  
4.  W dolnej części strony, wybierz **kod** przycisku.  
  
5.  Zastąp istniejący kod znaczników następujący kod znaczników.  
  
    ```  
    <%@ Import Namespace="Microsoft.SharePoint.ApplicationPages" %>  
    <%@ Register Tagprefix="SharePoint" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>  
    <%@ Register Tagprefix="Utilities" Namespace="Microsoft.SharePoint.Utilities" Assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>  
    <%@ Register Tagprefix="asp" Namespace="System.Web.UI" Assembly="System.Web.Extensions, Version=3.5.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" %>  
    <%@ Import Namespace="Microsoft.SharePoint" %>  
    <%@ Assembly Name="Microsoft.Web.CommandUI, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>  
    <%@ Page Language="C#" Inherits="Microsoft.SharePoint.WebControls.LayoutsPageBase" MasterPageFile="../_catalogs/masterpage/mybasic1.master" meta:progid="SharePoint.WebPartPage.Document" %>  
  
    <asp:Content ID="Main" ContentPlaceHolderID="ContentPlaceHolderMain" runat="server">  
    <img alt="My Image" longdesc="My image from images folder" src="../images/myimg1.png" />  
    </asp:Content>  
    ```  
  
6.  Zapisz zaktualizowane strony.  
  
## <a name="export-the-items-from-sharepoint"></a>Eksportuj elementy z programu SharePoint  
 Eksportuj elementy z programu SharePoint do pliku rozwiązania (wsp) programu SharePoint.  
  
#### <a name="to-export-items-from-sharepoint-designer"></a>Aby wyeksportować elementy z programu SharePoint Designer  
  
1.  W programie SharePoint Designer w okienku nawigacji wybierz **witryny zespołu** obiektu, a następnie na **lokacji** wstążki, wybierz **Zapisz jako szablon**.  
  
2.  W **Zapisz jako szablon** okna dialogowego wprowadź nazwę pliku i nazwa szablonu, wybierz opcję **dołączanie zawartości** pole wyboru, a następnie wybierz pozycję **OK** przycisku.  
  
     To jest zapisywany zawartości witryny w pliku wsp.  
  
3.  Po rozwiązaniu eksportuje, wybierz **galerii rozwiązań** łącze, aby wyświetlić listę plików dostępne rozwiązania.  
  
4.  Otwórz menu skrótów dla nowego pliku wsp, a następnie wybierz pozycję **cel Zapisz jako** zapisać go w systemie.  
  
## <a name="import-the-items-into-visual-studio"></a>Importowanie elementów do programu Visual Studio  
 Importowanie plików .wsp do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Po zaimportowaniu zawartości można dostosować go, Dodaj więcej elementów i następnie wdrożyć go.  
  
#### <a name="to-import-items-from-the-wsp-file-into-visual-studio"></a>Aby zaimportować elementy z pliku wsp do programu Visual Studio  
  
1.  W [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], Utwórz **Importowanie pakietu rozwiązań 2010 SharePoint** projektu.  
  
2.  Na **wybierz elementy do zaimportowania** w obszarze **modułu** w **typu** kolumny, zaznacz pola wyboru dla tylko pliki w poniższej tabeli do importu.  
  
    |Nazwa pliku|Opis|  
    |---------------|-----------------|  
    |_catalogsmasterpage\_|Niestandardowej strony wzorcowej.|  
    |images_|Plik obrazu w systemie plików programu SharePoint.|  
    |SitePages_|Strona witryny.|  
  
3.  Wybierz **Zakończ** przycisk, aby importować wybrane elementy.  
  
4.  W **Eksploratora rozwiązań**, wybierz _catalogsmasterpage\_ węzeł i ustaw wartość jego **Rozwiązywanie konfliktów wdrożenia** właściwości **automatyczne**.  
  
     Dzięki temu, upewnij się, że automatycznie rozwiązać wszystkie konflikty wdrażania.  
  
5.  Jeśli nowej strony wzorcowej ma taką samą nazwę jak istniejącej strony, upewnij się, czy istniejącej strony nie jest oznaczony jako stronę wzorcową domyślnej lub niestandardowej strony wzorcowej w programie SharePoint Designer.  
  
     Jeśli istniejącej strony wzorcowej jest oznaczona jako domyślna strona wzorcowa lub niestandardowej strony wzorcowej, wystąpi błąd wdrażania stwierdzający, że nie można usunąć strony wzorcowej. Aby uniknąć tego problemu, wykonaj następujące czynności:  
  
    -   Jeśli istniejące strony wzorcowej jest ustawiony jako domyślna strona wzorcowa, tymczasowo ustawić jako domyślna strona wzorcowa innej strony wzorcowej. Po wdrożeniu plików do programu SharePoint, należy ustawić nowej strony wzorcowej jako domyślna strona wzorcowa.  
  
    -   Jeśli istniejące strony wzorcowej jest ustawiony jako niestandardowej strony wzorcowej, tymczasowo ustawić innej strony wzorcowej jako niestandardowej strony wzorcowej. Po wdrożeniu plików do programu SharePoint, należy ustawić nowej strony wzorcowej jako niestandardowej strony wzorcowej.  
  
6.  Na pasku menu wybierz **kompilacji**, **wdrożyć rozwiązanie**.  
  
7.  Otwórz witrynę programu SharePoint, aby wyświetlić elementy wdrożone.  
  
 Alternatywny sposób importowanie plików do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] i wdrażać je do programu SharePoint jest dodanie plików w modułach [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][Porady: importowanie tematu lub strony wzorcowej](../sharepoint/how-to-import-a-master-page-or-theme.md) i [przy użyciu modułów podczas dołączania plików rozwiązania](../sharepoint/using-modules-to-include-files-in-the-solution.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Importowanie elementów z istniejącej witryny SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Tworzenie kontrolek wielokrotnego użytku dla części sieciowych lub stron aplikacji](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
  