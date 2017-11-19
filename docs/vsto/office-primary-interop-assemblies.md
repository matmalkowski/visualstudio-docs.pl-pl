---
title: "Podstawowe zestawy międzyoperacyjne pakietu Office | Dokumentacja firmy Microsoft"
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
- primary interop assemblies
- assemblies [Office development in Visual Studio], primary interop assemblies
- Office primary interop assemblies
ms.assetid: aa29d12c-185f-4558-a7cd-3d85f924203d
caps.latest.revision: "44"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8b97c44da9740d36ea68766c8dc0e56e535d5165
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="office-primary-interop-assemblies"></a>Podstawowe zestawy międzyoperacyjne pakietu Office
  Aby korzystać z funkcji aplikacji pakietu Microsoft Office z projektu pakietu Office, należy użyć podstawowy zestaw międzyoperacyjny (PIA) dla aplikacji. PIA umożliwia kodu zarządzanego do interakcji z modelu obiektowego oparte na modelu COM aplikacji pakietu Microsoft Office.  
  
 Podczas tworzenia nowego projektu pakietu Office Visual Studio dodaje odwołania do PIAs, które są wymagane, aby skompilować projekt. W niektórych scenariuszach może być konieczne dodanie odwołania do PIAs dodatkowe (na przykład, jeśli chcesz użyć funkcji programu Microsoft Office Word w projekcie dla programu Microsoft Office Excel).  
  
 W tym temacie opisano następujące aspekty w projektach pakietu Office przy użyciu Microsoft PIAs pakietu Office:  
  
-   [Do tworzenia i uruchamiania projektów oddzielne podstawowe zestawy międzyoperacyjne](#separateassemblies)  
  
-   [W jednym projekcie przy użyciu funkcji wiele aplikacji pakietu Microsoft Office](#usingfeatures)  
  
-   [Pełna lista podstawowe zestawy międzyoperacyjne aplikacji pakietu Microsoft Office](#pialist)  
  
 Aby uzyskać więcej informacji na temat podstawowe zestawy międzyoperacyjne zobacz [podstawowe zestawy międzyoperacyjne](http://msdn.microsoft.com/en-us/b977a8be-59a0-40a0-a806-b11ffba5c080).  
  
##  <a name="separateassemblies"></a>Oddziel podstawowe zestawy międzyoperacyjne do tworzenia i uruchamiania projektów  
 Visual Studio będzie korzystać różne zestawy PIAs na komputerze dewelopera. Te zestawy różnych zestawów znajdują się w następujących lokalizacjach:  
  
-   Folder w katalogu program files.  
  
     Te kopie zestawy są używane podczas pisania kodu i kompilacji projektów. Visual Studio automatycznie instaluje te zestawy.  
  
-   Globalna pamięć podręczna zestawów.  
  
     Te kopie zestawy są używane podczas niektórych zadań związanych z projektowaniem, np. podczas uruchamiania lub debugowania projektów. Program Visual Studio nie Zainstaluj i zarejestruj te zestawy; należy to robić samodzielnie.  
  
### <a name="primary-interop-assemblies-in-the-program-files-directory"></a>Podstawowe zestawy międzyoperacyjne w katalogu Program Files  
 Po zainstalowaniu programu Visual Studio PIAs są automatycznie instalowane w lokalizacji w systemie plików, poza globalnej pamięci podręcznej zestawów. Podczas tworzenia nowego projektu programu Visual Studio automatycznie dodaje odwołania do tych kopii PIAs do projektu. Visual Studio używa tych kopii PIAs, zamiast zestawów w globalnej pamięci podręcznej zestawów, do rozpoznania odwołania do typu, podczas tworzenia i skompilowanie projektu.  
  
 Te kopie PIAs pomocy programu Visual Studio uniknąć kilka problemów programowanie, które mogą wystąpić podczas różne wersje PIAs są zarejestrowane w globalnej pamięci podręcznej zestawów.  
  
 Visual Studio instaluje te kopie PIAs do poniższych lokalizacji na komputerze dewelopera:  
  
-   %ProgramFiles%\Microsoft Studio 12.0\Visual programu visual Studio Tools for Office\PIA\Office14  
  
     (lub % ProgramFiles (x86) %\Microsoft Visual Studio 12.0\Visual Studio Tools for Office\PIA\Office14 na 64-bitowych systemach operacyjnych)  
  
-   %ProgramFiles%\Microsoft Studio 12.0\Visual programu visual Studio Tools for Office\PIA\Office15  
  
     (lub % ProgramFiles (x86) %\Microsoft Visual Studio 12.0\Visual Studio Tools for Office\PIA\Office15 na 64-bitowych systemach operacyjnych)  
  
### <a name="primary-interop-assemblies-in-the-global-assembly-cache"></a>Podstawowe zestawy międzyoperacyjne w globalnej pamięci podręcznej zestawów  
 Do wykonania niektórych zadań związanych z projektowaniem, PIAs musi być zainstalowane i zarejestrowane w globalnej pamięci podręcznej zestawów na komputerze dewelopera. Zazwyczaj PIAs są instalowane automatycznie podczas instalowania pakietu Office na komputerze dewelopera. Aby uzyskać więcej informacji, zobacz [Konfigurowanie komputera na potrzeby programowania rozwiązań pakietu Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
 PIAs pakietu Office nie są wymagane na komputerach użytkowników końcowych do uruchamiania rozwiązań pakietu Office. Aby uzyskać więcej informacji, zobacz [projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md).  
  
##  <a name="usingfeatures"></a>W jednym projekcie przy użyciu funkcji wiele aplikacji pakietu Microsoft Office  
 Każdy szablon projektu pakietu Office w Visual Studio jest przeznaczona do pracy z jedną aplikację Microsoft Office. Aby korzystać z funkcji wiele aplikacji pakietu Microsoft Office lub korzystanie z funkcji w aplikacji lub składnika, który nie ma projektu w programie Visual Studio, musi Dodaj odwołanie do PIAs wymagane.  
  
 W większości przypadków należy dodać odwołania do PIAs, zainstalowanych przez program Visual Studio w obszarze %ProgramFiles%\Microsoft Visual Studio 12.0\Visual Studio Tools dla katalogu Office\PIA\. Te wersje zestawy są wyświetlane na **Framework** karty **odwołania Menedżer** okno dialogowe. Aby uzyskać więcej informacji, zobacz [porady: docelowy Office aplikacji za pośrednictwem podstawowe zestawy międzyoperacyjne](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md).  
  
 Jeśli masz zainstalowany i zarejestrowany PIAs w globalnej pamięci podręcznej zestawów, tych wersji zestawy są wyświetlane na **COM** karcie **Menedżera odwołań** okno dialogowe. Dodawanie odwołań do tych wersji zestawów, należy unikać, ponieważ istnieją programowanie problemy, które mogą wystąpić podczas używania ich. Na przykład, jeśli różne wersje PIAs zostały zarejestrowane w globalnej pamięci podręcznej zestawów, projekt będzie automatycznie wiązane z wersja zestawu, który został ostatnio zarejestrowany — nawet wtedy, gdy Określ inną wersję zestawu na  **COM** karcie **Menedżera odwołań** okno dialogowe.  
  
> [!NOTE]  
>  Niektóre zestawy są automatycznie dodawane do projektu po dodaniu zestawie, do którego odwołuje się do nich. Na przykład odwołania do zestawów Office.dll i Microsoft.Vbe.Interop.dll są dodawane automatycznie podczas dodawania odwołania do zestawów programu Word, Excel, Outlook, Microsoft Forms lub wykres.  
  
##  <a name="pialist"></a>Podstawowe zestawy międzyoperacyjne aplikacji pakietu Microsoft Office  
 W poniższej tabeli przedstawiono podstawowe zestawy międzyoperacyjne, które są dostępne dla [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] i [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)].  
  
|Office aplikacji lub składnika|Nazwa podstawowego zestawu międzyoperacyjnego|  
|-------------------------------------|-----------------------------------|  
|Program Microsoft Access 14.0 biblioteki obiektów<br /><br /> Biblioteki obiektów programu Microsoft Access 15.0|Microsoft.Office.Interop.Access.dll|  
|Microsoft Office 14.0 dostępu do bazy danych aparatu biblioteki<br /><br /> Microsoft Office 15.0 dostępu do bazy danych aparatu biblioteki|Microsoft.Office.Interop.Access.Dao.dll|  
|Biblioteka programu Microsoft Excel 14.0<br /><br /> Biblioteka programu Microsoft Excel 15.0|Microsoft.Office.Interop.Excel.dll|  
|Microsoft Graph 14.0 obiektu biblioteki (używane przez program PowerPoint, dostępu i Word dla wykresów)<br /><br /> Biblioteka Microsoft Graph 15.0|Microsoft.Office.Interop.Graph.dll|  
|Program Microsoft InfoPath 2.0 biblioteki typów (tylko InfoPath 2007)|Microsoft.Office.Interop.InfoPath.dll|  
|Program Microsoft InfoPath XML zestawu międzyoperacyjnego (dla tylko InfoPath 2007)|Microsoft.Office.Interop.InfoPath.Xml.dll|  
|Biblioteki obiektów 14.0 pakietu Microsoft Office (Office udostępnionych funkcji)<br /><br /> Biblioteki obiektów 15.0 pakietu Microsoft Office (Office udostępnionych funkcji)|Office.dll|  
|Microsoft Office Outlook widoku Control (pozwala na stronach sieci Web i aplikacji dostęp do skrzynki odbiorczej)|Microsoft.Office.Interop.OutlookViewCtl.dll|  
|Biblioteka programu Microsoft Outlook 14.0<br /><br /> Biblioteka programu Microsoft Outlook 15.0|Microsoft.Office.Interop.Outlook.dll|  
|Biblioteka programu Microsoft PowerPoint 14.0<br /><br /> Biblioteka programu Microsoft PowerPoint 15.0|Microsoft.Office.Interop.PowerPoint.dll|  
|Biblioteka programu Microsoft Project 14.0<br /><br /> Biblioteka programu Microsoft Project 15.0|Microsoft.Office.Interop.MSProject.dll|  
|Biblioteka programu Microsoft Publisher 14.0<br /><br /> Biblioteka programu Microsoft Publisher 15.0|Microsoft.Office.Interop.Publisher.dll|  
|Odwołanie do biblioteki sieci Web programu Microsoft SharePoint Designer 14.0|Microsoft.Office.Interop.SharePointDesigner.dll|  
|Biblioteka odwołanie do obiektu strony programu Microsoft SharePoint Designer 14.0|Microsoft.Office.Interop.SharePointDesignerPage.dll|  
|Biblioteki typów 2.0 inteligentne tagi Microsoft **Uwaga:** tagi inteligentne nie są używane w [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] i [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].|Microsoft.Office.Interop.SmartTag.dll|  
|Program Microsoft Visio 14.0 biblioteki typów<br /><br /> Program Microsoft Visio 15.0 biblioteki typów|Microsoft.Office.Interop.Visio.dll|  
|Program Microsoft Visio 14.0 Zapisz jako biblioteki typów sieci Web<br /><br /> Program Microsoft Visio 15.0 Zapisz jako biblioteki typów sieci Web|Microsoft.Office.Interop.Visio.SaveAsWeb.dll|  
|Biblioteki typu formantu rysowania programu Microsoft Visio 14.0<br /><br /> Biblioteki typu formantu rysowania programu Microsoft Visio 15.0|Microsoft.Office.Interop.VisOcx.dll|  
|Biblioteka programu Microsoft Word 14.0<br /><br /> Biblioteka programu Microsoft Word 15.0|Microsoft.Office.Interop.Word.dll|  
|Microsoft Visual Basic for Applications Extensibility 5.3|Microsoft.Vbe.Interop.dll|  
  
### <a name="binding-redirect-assemblies"></a>Zestawy przekierowanie powiązania  
 Po zainstalowaniu i zarejestrować PIAs pakietu Office w globalnej pamięci podręcznej zestawów (lub z pakietu Office, instalując pakiet redystrybucyjny dla PIAs), zestawy przekierowania powiązania są również instalowane tylko w globalnej pamięci podręcznej zestawów. Te zestawy upewnić się, że poprawną wersję podstawowe zestawy międzyoperacyjne zostały załadowane w czasie wykonywania. Na przykład, gdy rozwiązanie, która odwołuje się [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] zestawu działa na komputerze, który ma [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] powoduje, że przekierowanie powiązania zestawu wersji tego samego podstawowego zestawu międzyoperacyjnego, [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] środowiska uruchomieniowego załadować [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] Wersja podstawowego zestawu międzyoperacyjnego. Aby uzyskać więcej informacji, zobacz [porady: Włączanie i wyłączanie automatycznego przekierowania powiązania](/dotnet/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection).  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: docelowa aplikacji pakietu Office za pośrednictwem podstawowe zestawy międzyoperacyjne](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [Model obiektu Excel ― omówienie](../vsto/excel-object-model-overview.md)   
 [InfoPath — rozwiązania](../vsto/infopath-solutions.md)   
 [Model obiektu Outlook ― omówienie](../vsto/outlook-object-model-overview.md)   
 [PowerPoint — rozwiązania](../vsto/powerpoint-solutions.md)   
 [Rozwiązania projektu](../vsto/project-solutions.md)   
 [Model obiektu Visio ― omówienie](../vsto/visio-object-model-overview.md)   
 [Przegląd modelu obiektów programu Word](../vsto/word-object-model-overview.md)   
 [Informacje ogólne &#40; programowanie Office w Visual Studio &#41;](../vsto/general-reference-office-development-in-visual-studio.md)  
  
  