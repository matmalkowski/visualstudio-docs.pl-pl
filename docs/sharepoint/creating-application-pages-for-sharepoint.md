---
title: Tworzenie stron aplikacji dla programu SharePoint | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, Web pages
- SharePoint development in Visual Studio, content pages
- SharePoint development in Visual Studio, application pages
- application pages [SharePoint development in Visual Studio], developing
- application pages [SharePoint development in Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8bc73918a2af82acab1fd465f5f80755cc594ba9
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34691982"
---
# <a name="creating-application-pages-for-sharepoint"></a>Tworzenie stron aplikacji dla SharePoint
  *Strony aplikacji* prowadzi do strony sieci Web ASP.NET, który jest przeznaczony do użytku w witrynie sieci Web programu SharePoint. Strony aplikacji są specjalistyczną odmianą strony ASP.NET. Główną różnicą między aplikacji i standardowe strony ASP.NET jest, że strony aplikacji zawiera zawartość, która jest scalany z strony wzorcowej programu SharePoint. Strona wzorcowa umożliwia stron aplikacji do udostępniania tego samego wygląd i zachowanie jako innych stron w witrynie.  
  
 Program Visual Studio pozwala projektować stron aplikacji za pomocą projektanta. Projektant wyświetla obszar zawartości każdego symbolu zastępczego zawartości, która jest zdefiniowana w strony wzorcowej. Strony aplikacji można projektować, przeciągając kontrolek do tych obszarów zawartości.  
  
## <a name="application-pages"></a>Strony aplikacji
 Strony aplikacji są współużytkowane przez wszystkich witryn na serwerze, strony witryny jest specyficzne dla jednej lokacji. Aby uzyskać więcej informacji [typów strony programu SharePoint](http://go.microsoft.com/fwlink/?LinkID=211584).  
  
 Domyślnie większość stron, które pojawiają się podczas tworzenia witryny programu SharePoint są stron witryny. Strona lokacji można dodać do biblioteki programu SharePoint strony. Użytkownicy mogą dostosowywać strony witryny za pomocą narzędzi, takich jak SharePoint Designer. Strona witryny może również obsługiwać funkcje, takie jak dynamiczne części sieci Web i strefy składników Web Part.  
  
 Stron aplikacji nie może wykonać te czynności. Jednak najlepszym typem strony do utworzenia, jeśli strona zawiera kod niestandardowy jest strony aplikacji. Mimo że można dodać kod niestandardowy do strony witryny, kod zatrzymane, kiedy użytkownik dostosowuje strony za pomocą narzędzi, takich jak SharePoint Designer.  
  
> [!NOTE]  
>  Program Visual Studio nie udostępnia szablonów, które ułatwiają tworzenie stron witryny witryny programu SharePoint. Aby uzyskać więcej informacji, zobacz [typów strony programu SharePoint](http://go.microsoft.com/fwlink/?LinkID=211584).  
  
## <a name="create-an-application-page"></a>Tworzenie strony aplikacji
 Aby utworzyć stronę aplikacji, należy dodać **strony aplikacji** elementu projektu SharePoint. Po utworzeniu strony aplikacji programu Visual Studio dodaje następujące foldery do projektu:  
  
|Folder|Opis|  
|------------|-----------------|  
|Układy|Mapowany do katalogu wirtualnego _layouts systemu plików programu SharePoint.|  
|Podfolder układów|Zawiera pliki, które składają się na stronie aplikacji. Domyślnie ten folder ma taką samą nazwę jak projektu. W dowolnym momencie można zmienić nazwę tego folderu. Po uruchomieniu projektu programu Visual Studio wdraża tego folderu do katalogu wirtualnego _layouts systemu plików programu SharePoint.|  
  
 Visual Studio dodaje następujące pliki do projektu:  
  
|Plik|Opis|  
|----------|-----------------|  
|Plik strony ASP.NET (aspx)|Zawiera kod znaczników XML, który definiuje stronę.|  
|Plik kodu strony aplikacji|Zawiera kod związany z strony aplikacji. Dodaj kod, który obsługuje zdarzenia do tego pliku.|  
|Plik kodu projektanta strony aplikacji|Zawiera kod, który jest generowany przez projektanta. Nie należy bezpośrednio edytować ten plik.|  
  
## <a name="design-and-debug-an-application-page"></a>Projektowanie i debugowanie strony aplikacji
 Projektowanie zawartości strony aplikacji przy użyciu narzędzia Projektant widok w programie Visual Studio. Ten Projektant pojawia się po otwarciu strony aplikacji w projekcie (kliknij go dwukrotnie lub otwieranie menu skrótów, a następnie wybierając **Otwórz**), a następnie wybierz **projekt** przycisk w dolnej części Edytor.  
  
> [!NOTE]  
>  Można zaprojektować strony tylko w **źródła** Widok projektanta. **Projekt** Widok projektanta jest wyłączone dla stron aplikacji.  
  
 Strony aplikacji można debugować tak samo, jak może debugować innych elementów projektu SharePoint w Visual Studio. Po uruchomieniu debugera programu Visual Studio Visual Studio otworzy w witrynie programu SharePoint.  
  
 Aby wyświetlić stronę aplikacji, musisz ręcznie przejść do lokalizacji strony aplikacji (na przykład: http://*nazwa_serwera*folderze /_layouts/*Project_Name*/ApplicationPage1.aspx).  
  
 Aby uzyskać więcej informacji na temat debugowania projektów SharePoint, zobacz [Rozwiązywanie problemów z rozwiązań SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
## <a name="choose-a-master-page"></a>Wybierz stronę wzorcową
 Domyślnie **strony aplikacji** elementu odwołuje się do witryny, którego używasz do debugowania projektu strony wzorcowej. Czy strona ma nazwę v4.master i znajduje się ona na liście **galerii stron wzorcowych** witryny programu SharePoint.  
  
 Jawnie zmiany, które strony wzorcowej jest używany przez stronę aplikacji, ustawiając `MasterPageFile` atrybutu aplikacji `Page` elementu. (Na przykład: `MasterPageFile="~/_layouts/applicationv4.master"`). W rzeczywistości należy ustawić ten atrybut, jeśli strony wzorcowej dynamiczne nie są włączone na serwerze programu SharePoint. Aby uzyskać więcej informacji na temat stron wzorcowych w programie SharePoint, zobacz [stron wzorcowych](http://go.microsoft.com/fwlink/?LinkID=169281).  
  
## <a name="see-also"></a>Zobacz także
 [Projektowanie SharePoint Foundation w głębokość](http://go.microsoft.com/fwlink/?LinkID=182103)   
 [Omówienie programu ASP.NET](/aspnet/overview)   
 [ASP.NET Web Pages](/aspnet/web-pages/index)   
  
