---
title: 'Przykładowe rozszerzenie programu Excel: Klasy elementów | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 1dce9745db1acf031c67d5221f6a176d94fb6f77
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="sample-excel-extension-element-classes"></a>Przykładowe rozszerzenie programu Excel: klasy elementów
Rozszerzenie używa klas pochodzących z <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> i reprezentują komórki formantu w i kontroli arkusza [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)].

 Element podstawowy dla tego rozszerzenia jest `ExcelElement`. `ExcelWorksheetElement` Klasy i `ExcelCellElement` klasa dziedziczy z elementu

## <a name="element-and-elementinformation-classes"></a>Element i ElementInformation klasy
 `Element` Jest klasa podstawowa dla wszystkich elementów interfejsu użytkownika dla rozszerzenia programu Excel, a dziedziczy on z <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> klasy. `ElementInformation` jest klasą bazową dla elementu klasy informacji w próbce, a nie ma członków.

#### <a name="simple-properties-and-methods"></a>Proste właściwości i metody
 Te elementy Członkowskie zwracają wartości prostego, takich jak wartość `Name` właściwości lub wartości `ClassName` właściwości oraz kod jest czysty i łatwy do odczytania. Niektóre wartości są zwracane za pomocą `Utility` klasy, która została omówiona później. Inne zwracać `null` ponieważ nie są odpowiednie w tym rozszerzeniu próbki. Dwa elementy członkowskie są bardziej interesującego od innych: <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A> właściwości i <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.CacheProperties%2A> metody.

#### <a name="queryid-property"></a>Właściwość identyfikatora kwerendy
 Ta właściwość zwraca warunek, który składa się z pary nazwa wartość właściwości, które jednoznacznie identyfikują formant podczas odtwarzania. Dla każdej klasy pochodnej kontroli deweloper musi przesłonić tę właściwość, aby zwrócić <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement> obiektów w ramach za pomocą odnaleźć formantu w interfejsie użytkownika.

#### <a name="cacheproperties-method"></a>CacheProperties — metoda
 Ta metoda jest wywoływana przez platformę testowych podczas procesu rejestrowania stwierdzić, Zapisz migawkę ważne właściwości elementu. Dzięki temu właściwości dostępne nawet wtedy, gdy rzeczywista formantu interfejsu użytkownika nie jest już na ekranie.

## <a name="worksheetelement-and-worksheetinformation-classes"></a>Klasy WorksheetInformation i WorksheetElement
 `WorksheetElement` Klasy reprezentuje arkuszu programu Excel w ramach testowania i dziedziczy `Element` klasy podstawowej. Trzy właściwości zostały zastąpione podające określone informacje o obiekcie arkuszu programu Excel: <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.ClassName%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.ControlTypeName%2A>, i <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.Name%2A>.

 <xref:System.Runtime.InteropServices.ComVisibleAttribute> Jest również stosowane do tej klasy, aby była widoczna dla modelu COM.

 `WorksheetInformation` Klasa reprezentuje informacje o arkuszu programu Excel. Ma ona tylko jeden element członkowski, `SheetName` właściwość, która jest wystarczająca dla tego przykładu.

## <a name="cellelement-and-cellinformation-classes"></a>Klasy CellInformation i CellElement
 `CellElement` Klasy reprezentuje komórki w programie Excel, a dziedziczy `Element` klasy podstawowej. Jest tylko zastąpionym elementem członkowskim <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A> właściwość, która zwraca <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement> używającą `RowIndex` i `ColumnIndex` właściwości w celu zidentyfikowania komórki.

## <a name="utilities-and-excelutilities-classes"></a>Narzędzia i ExcelUtilities klas
 Wewnętrznej `ExcelUtilities` klasa udostępnia wartości stałych, takie jak nazwa technologii i metody, która określa, czy uchwytu okna podana reprezentuje arkuszu programu Excel.

 `Utilities` Klasa zawiera metody pomocnicze, które zwracają różne informacje o Interfejsie użytkownika. W przypadku niektórych metod Użyj bezpośrednie wywołania do systemu zewnętrznego bibliotek DLL, takiego jak **USER32. Biblioteki DLL** i **OLEACC. Biblioteki DLL**, aby uzyskać dojścia do okna z interfejsu użytkownika**.**

## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.ComVisibleAttribute>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement>
- [Rozszerzanie kodowanych testów interfejsu użytkownika i rejestrowanie akcji obsługujących program Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
