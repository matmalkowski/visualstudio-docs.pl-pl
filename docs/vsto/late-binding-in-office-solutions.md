---
title: "Późne wiązania w rozwiązaniach pakietu Office | Dokumentacja firmy Microsoft"
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
- objects [Office development in Visual Studio], casting
- types [Office development in Visual Studio], casting
- automation [Office development in Visual Studio], casting objects
- casting, object to specific type
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 430c10ffa5f79be45282d637b48772943be638e9
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="late-binding-in-office-solutions"></a>Późne powiązania w rozwiązaniach pakietu Office
  Niektóre typy modeli obiektów w aplikacji pakietu Office zawierają funkcje, które są dostępne za pośrednictwem funkcji późnego wiązania. Na przykład niektóre metody i właściwości może zwracać różne typy obiektów, w zależności od kontekstu aplikacji pakietu Office, a niektóre typy mogą uwidaczniać różne metody lub właściwości w różnych kontekstach.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Where projekty Visual Basic **Option Strict** jest wyłączone i Visual C# projektów przeznaczonych [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] może współpracować bezpośrednio z typów, korzystających z tych funkcji późnego wiązania.  
  
## <a name="implicit-and-explicit-casting-of-object-return-values"></a>Jawne i niejawne rzutowanie obiektów zwracanych wartości  
 Wiele metod i właściwości pakietu Microsoft Office, zwróć podstawowe zestawy międzyoperacyjne (PIAs) <xref:System.Object> wartości, ponieważ zwracają kilka różnych typów obiektów. Na przykład <xref:Microsoft.Office.Tools.Excel.Workbook.ActiveSheet%2A> zwraca <xref:System.Object> ponieważ jej wartość zwrotna może być <xref:Microsoft.Office.Interop.Excel.Worksheet> lub <xref:Microsoft.Office.Interop.Excel.Chart> obiektu, w zależności od tego, co to jest aktywnym arkuszu.  
  
 Gdy metoda lub właściwość zwraca <xref:System.Object>, jawnie przekonwertuj (w języku Visual Basic) obiektu poprawnego typu w projektach Visual Basic gdzie **Option Strict** znajduje się na. Nie trzeba jawnie rzutowania <xref:System.Object> zwracają wartości w projektach Visual Basic gdzie **Option Strict** jest wyłączona.  
  
 W większości przypadków dokumentacji referencyjnej zawiera typy zwracane wartości dla elementu członkowskiego, który zwraca <xref:System.Object>. Konwertowanie albo rzutowanie obiektu włącza IntelliSense dla obiekt w edytorze kodu.  
  
 Aby uzyskać informacje o konwersji w języku Visual Basic, zobacz [niejawnych i jawnych konwersji &#40; Visual Basic &#41; ](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions) i [funkcji CType &#40; Visual Basic &#41; ](/dotnet/visual-basic/language-reference/functions/ctype-function).  
  
### <a name="examples"></a>Przykłady  
 Poniższy przykład kodu pokazuje, jak można rzutować obiektu określonego typu w projektach Visual Basic gdzie **Option Strict** znajduje się na. W tym typie projektu, należy jawnie rzutować <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> właściwości <xref:Microsoft.Office.Interop.Excel.Range>. W tym przykładzie wymaga projektu poziomie dokumentu programu Excel z arkusza klasę o nazwie `Sheet1`.  
  
 [!code-vb[Trin_VstcoreProgramming#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#9)]  
  
 W poniższym przykładzie pokazano, jak niejawnie rzutowania obiektu określonego typu w projektach Visual Basic gdzie **Option Strict** jest wyłączony lub w projektach Visual C#, którego celem jest [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. W przypadku tych typów projektów <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> właściwości niejawnie jest rzutowane na <xref:Microsoft.Office.Interop.Excel.Range>. W tym przykładzie wymaga projektu poziomie dokumentu programu Excel z arkusza klasę o nazwie `Sheet1`.  
  
 [!code-vb[Trin_VstcoreProgramming#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#10)]
 [!code-csharp[Trin_VstcoreProgramming#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/Sheet1.cs#10)]  
  
## <a name="accessing-members-that-are-available-only-through-late-binding"></a>Uzyskiwanie dostępu do elementów członkowskich, które są dostępne tylko za pośrednictwem późne wiązanie  
 Niektóre właściwości i metody w PIAs pakietu Office są dostępne tylko za pośrednictwem późnego wiązania. W języku Visual Basic, projekty where **Option Strict** jest wyłączony lub w projektach Visual C# kierowanych [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], umożliwia funkcji późne wiązania w tych językach dostęp do elementów członkowskich z późnym wiązaniem. W języku Visual Basic, projekty where **Option Strict** jest włączone, aby dostęp do tych elementów członkowskich, należy użyć odbicia.  
  
### <a name="examples"></a>Przykłady  
 W poniższym przykładzie pokazano, jak dostęp do elementów członkowskich późno powiązanym w projektach Visual Basic gdzie **Option Strict** jest wyłączony lub w projektach Visual C#, którego celem jest [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. W tym przykładzie uzyskuje dostęp do późnym wiązaniem **nazwa** właściwość **Otwórz plik** okno dialogowe w programie Word. Aby użyć tego przykładu, uruchom go z `ThisDocument` lub `ThisAddIn` klasy w projekcie programu Word.  
  
 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-csharp[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]  
  
 Poniższy przykład kodu pokazuje sposób użycia odbicia do wykonania tego samego zadania w projektach Visual Basic gdzie **Option Strict** znajduje się na.  
  
 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]  
  
## <a name="see-also"></a>Zobacz też  
 [Pisanie kodu dla rozwiązań pakietu Office](../vsto/writing-code-in-office-solutions.md)   
 [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Przy użyciu typu dynamicznego &#40; K & 35; Przewodnik programowania w języku &#41;](/dotnet/csharp/programming-guide/types/using-type-dynamic)   
 [Option Strict — instrukcja](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Odbicie (C#)](/dotnet/csharp/programming-guide/concepts/reflection)  
 [Odbicie (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)  
 [Projektowanie i tworzenie rozwiązań Office](../vsto/designing-and-creating-office-solutions.md)  
  
  