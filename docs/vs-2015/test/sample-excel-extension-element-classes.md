---
title: 'Przykładowe rozszerzenie programu Excel: Klasy elementów | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c251098-00aa-49cf-9e37-5717c0c6b3f1
caps.latest.revision: 11
ms.author: gewarren
manager: douge
ms.openlocfilehash: 0babaf7e387f9255dc8a60958483ba9db66cc879
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42684039"
---
# <a name="sample-excel-extension-element-classes"></a>Przykładowe rozszerzenie programu Excel: klasy elementów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [Przykładowe rozszerzenie programu Excel: klasy elementów](https://docs.microsoft.com/visualstudio/test/sample-excel-extension-element-classes).  
  
Rozszerzenie używa klas, które są uzyskiwane z <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> i reprezentują kontroli arkusza i kontrola komórki w [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)].  
  
 Element podstawowy dla tego rozszerzenia jest `ExcelElement`. `ExcelWorksheetElement` Klasy i `ExcelCellElement` klasa dziedziczy ten element  
  
## <a name="element-and-elementinformation-classes"></a>Element i ElementInformation klasy  
 `Element` Jest klasą bazową dla wszystkich elementów interfejsu użytkownika dla rozszerzenia programu Excel i dziedziczy <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> klasy. `ElementInformation` jest klasą bazową dla elementu klasy informacji w przykładzie, a nie ma członków.  
  
#### <a name="simple-properties-and-methods"></a>Proste właściwości i metod  
 Te składowe zwracają wartości prostego, takich jak wartość `Name` właściwość lub wartość `ClassName` właściwości i kod jest przejrzysta i łatwa do odczytania. Niektóre wartości są zwracane przez przy użyciu `Utility` klasy, która została omówiona w dalszej części. Osobom wróć `null` ponieważ nie są istotne w tym rozszerzeniu próbki. Dwa elementy członkowskie są bardziej interesujące niż pozostałe: <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A> właściwości i <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.CacheProperties%2A> metody.  
  
#### <a name="queryid-property"></a>Właściwość QueryId  
 Ta właściwość zwraca warunek, który składa się z pary nazwa wartość właściwości, które jednoznacznie identyfikują kontrolki podczas odtwarzania. Dla każdej klasy pochodnej kontrolki jest Deweloper przesłonięcie tę właściwość, aby zwrócić <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement> obiektu, że struktura umożliwia znalezienie formantu w interfejsie użytkownika.  
  
#### <a name="cacheproperties-method"></a>Metoda CacheProperties  
 Ta metoda jest wywoływana przez strukturę testów podczas procesu rejestrowania mówić element, aby zapisać migawkę ważne właściwości. Przechowuje właściwości dostępne, nawet wtedy, gdy jest to rzeczywiste kontrolki interfejsu użytkownika nie jest już na ekranie.  
  
## <a name="worksheetelement-and-worksheetinformation-classes"></a>Klasy WorksheetInformation i WorksheetElement  
 `WorksheetElement` Klasa reprezentuje arkusza programu Excel w taki sposób, w ramach testowania i dziedziczy z `Element` klasy bazowej. Trzy właściwości zostaną zastąpione, podające określone informacje o obiekcie arkusza programu Excel: <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.ClassName%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.ControlTypeName%2A>, i <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.Name%2A>.  
  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute> Jest również zastosowane do tej klasy, aby była widoczna dla modelu COM.  
  
 `WorksheetInformation` Klasa przedstawia informacje o arkuszu programu Excel. Ma ona tylko jednego członka `SheetName` właściwość, która jest wystarczająca na potrzeby tego przykładu.  
  
## <a name="cellelement-and-cellinformation-classes"></a>Klasy CellInformation i CellElement  
 `CellElement` Klasa reprezentuje komórki programu Excel i dziedziczy z `Element` klasy bazowej. Jest tylko zgodnym z przesłoniętą składową <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A> właściwość, która zwraca <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement> , który używa `RowIndex` i `ColumnIndex` właściwości w celu zidentyfikowania komórki.  
  
## <a name="utilities-and-excelutilities-classes"></a>Narzędzia i ExcelUtilities klas  
 Wewnętrzny `ExcelUtilities` klasa udostępnia niektóre wartości stałych, takich jak nazwa technologii i metody, która określa, czy uchwyt okna podana reprezentuje arkusza programu Excel.  
  
 `Utilities` Klasa zawiera metody pomocnicze, które zwracają różne informacje o Interfejsie użytkownika. Niektóre metody używają bezpośrednich wywołań do systemu zewnętrznego bibliotek DLL, **USER32. Biblioteka DLL** i **OLEACC. Biblioteka DLL**, można uzyskać dojścia do okna z interfejsu użytkownika **.**  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement>   
 [Rozszerzanie kodowanych testów interfejsu użytkownika i rejestrowanie akcji obsługujących program Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)



