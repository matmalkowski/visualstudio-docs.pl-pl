---
title: Tworzenie stron dla SharePoint | Dokumentacja firmy Microsoft
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
- SharePoint development in Visual Studio, master pages
- SharePoint development in Visual Studio, page layouts
- SharePoint development in Visual Studio, content pages
- master pages[SharePoint development in Visual Studio], designing
- content pages[SharePoint development in Visual Studio], designing
- page layouts[SharePoint development in Visual Studio], designing
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 4b65c601d36dd04d95466fc8f8dff7a95b70c44a
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="creating-pages-for-sharepoint"></a>Tworzenie stron dla SharePoint
  Można utworzyć strony aplikacji, stron w witrynie, stron wzorcowych i układy stron witryny programu SharePoint.  
  
 Strony aplikacji można utworzyć za pomocą szablonu w programie Visual Studio. Tworzenie stron w witrynie, stron wzorcowych i układy stron, za pomocą programu SharePoint Designer. Następnie można zaimportować te strony do programu Visual Studio z nich korzystać w projekcie programu SharePoint.  
  
 Można również zmodyfikować wygląd i działanie stron przy użyciu kaskadowych arkuszy stylów, ECMAScript i motywów.  
  
## <a name="types-of-sharepoint-pages"></a>Typy strony programu SharePoint  
 W poniższej tabeli opisano cztery typy stron, które zawiera witryny programu SharePoint.  
  
|Typ strony|Opis|  
|---------------|-----------------|  
|Strony aplikacji|Tworzenie strony aplikacji, jeśli strona ma zawierać kod niestandardowy lub strona ma być udostępniane w wielu lokacjach. W przeciwnym razie strony witryny może być najlepszym rozwiązaniem.|  
|Strony witryny|Utwórz stronę lokacji, jeśli chcesz wykonać dowolną z następujących czynności:<br /><br /> -Dodaj stronę do biblioteki programu SharePoint.<br />-Włącz stronie do hosta funkcji, takich jak dynamicznych części sieci Web i strefy składników Web Part.<br />— Użytkownicy mogą dostosować stronę przy użyciu programu SharePoint Designer.<br /><br /> Nie należy tworzyć strony witryny, jeśli strona zawiera kod niestandardowy. Mimo że można dodać kod niestandardowy do strony witryny, kod zatrzymane, kiedy użytkownik dostosowuje strony za pomocą programu SharePoint Designer.|  
|Strony główne|Tworzenie strony głównej, jeśli chcesz zdefiniować wspólnej struktury strony witryny i stron aplikacji.|  
|Układy stron|Układy stron są specyficzne dla [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] i umożliwiają uściślić wspólnej struktury witryny i stron aplikacji.|  
  
 Omówienie każdego typu strony, zobacz [bloków konstrukcyjnych: stron i interfejs użytkownika](http://go.microsoft.com/fwlink/?LinkID=182095), i [układy stron i stron wzorcowych](http://go.microsoft.com/fwlink/?LinkID=182096).  
  
## <a name="creating-application-pages"></a>Tworzenie stron aplikacji  
 Można utworzyć strony aplikacji w programie Visual Studio, dodając **strony aplikacji** elementu do projektu programu SharePoint. Na stronie Dodaj formanty i następnie obsługę zdarzeń formantu przez dodanie kodu.  
  
 Można ustawić punkty przerwania w pliku kodu strony, uruchomienia debugera i przetestować w lokalnej witrynie programu SharePoint bez żadnych dodatkowych czynności konfiguracyjnych. Aby uzyskać więcej informacji, zobacz [tworzenie stron aplikacji dla programu SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
## <a name="creating-site-pages-master-pages-and-page-layouts"></a>Tworzenie stron w witrynie, stron wzorcowych i układy stron  
 Można utworzyć strony witryny, stron wzorcowych i układy stron za pomocą programu SharePoint Designer. Następnie można zaimportować te strony do programu Visual Studio. Jeśli chcesz skorzystać z wdrożenia lub funkcje kontroli źródła, które są dostępne w programie Visual Studio, należy zaimportować strony. Aby uzyskać więcej informacji, zobacz [Importowanie elementów z istniejącej witryny SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).  
  
 Ponieważ jest trudne do modyfikowania tych stron po ich zaimportowaniu, przed ich zaimportowaniem należy projektować te strony.  
  
## <a name="creating-cascading-style-sheets-ecmascript-and-themes"></a>Tworzenie kaskadowych arkuszy stylów, ECMAScript i motywów  
 Visual Studio nie ma szablonów dla tworzenie kaskadowych arkuszy stylów (CSS), ECMAScript (JavaScript, JScript) lub pliki motyw witryny programu SharePoint. Pliki te można utworzyć za pomocą wskazówki, które są dostępne w zestawie SDK programu SharePoint lub za pomocą narzędzi, takich jak SharePoint Designer.  
  
 Te pliki można dodać bezpośrednio do rozwiązania lub można je zaimportować. W obu przypadkach należy utworzyć odpowiednie foldery zamapowanego dla każdego elementu, który zostanie dodany. Aby uzyskać więcej informacji na temat tworzenia zamapowany folder, zobacz [porady: Dodawanie i usuwanie folderów mapowane](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
 Aby uzyskać więcej informacji o tworzeniu kaskadowych arkuszy stylów, zobacz [kaskadowych styl arkusze klasy użycia w programie SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkID=182098). Aby uzyskać więcej informacji o tworzeniu plików JavaScript i JScript dla rozwiązania programu SharePoint, zobacz [ustawienia zapasowej ASPX strony podstawowej dla języka ECMAScript](http://go.microsoft.com/fwlink/?LinkID=182099). Aby uzyskać więcej informacji na temat tematów, zobacz [bloków konstrukcyjnych: stron i interfejs użytkownika](http://go.microsoft.com/fwlink/?LinkID=182095).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Tworzenie stron aplikacji dla SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)|Opisuje sposób dodawania strony aplikacji: zawartość .aspx, która jest scalany z strony wzorcowej programu SharePoint.|  
|[Instrukcje: Tworzenie strony aplikacji](../sharepoint/how-to-create-an-application-page.md)|Pokazuje, jak utworzyć stron ASP.NET, które są uruchamiane w witrynie programu SharePoint.|  
|[Przewodnik: Tworzenie strony aplikacji SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)|Pokazuje, jak projektować i debugowania na stronie sieci Web platformy ASP.NET dla witryny programu SharePoint.|  
  
  