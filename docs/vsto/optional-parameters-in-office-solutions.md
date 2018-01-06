---
title: "Parametry opcjonalne w rozwiązaniach pakietu Office | Dokumentacja firmy Microsoft"
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
- Office applications [Office development in Visual Studio], optional parameters
- Visual C# [Office development in Visual Studio], optional parameters
- Visual Basic [Office development in Visual Studio], optional parameters
- application development [Office development in Visual Studio], optional parameters
- missing field [Office development in Visual Studio]
- optional parameters [Office development in Visual Studio]
- parameters [Office development in Visual Studio], optional
ms.assetid: 109eaef6-08bb-4b59-a29e-921f856027cc
caps.latest.revision: "43"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 3df07b6f60d4b870c830fc419b88decbe2f8fde1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="optional-parameters-in-office-solutions"></a>Parametry opcjonalne w rozwiązaniach Office
  Wiele metod modele obiektów w aplikacji pakietu Microsoft Office akceptuje następujące parametry opcjonalne. Jeśli używasz programu Visual Basic umożliwiające tworzenie rozwiązań pakietu Office w Visual Studio nie trzeba przekazać wartość następujące parametry opcjonalne, ponieważ zostaną automatycznie użyte wartości domyślne dla każdego parametru brak. W większości przypadków można również pominąć następujące parametry opcjonalne w projektach Visual C#. Jednak nie można pominąć opcjonalne **ref** parametry `ThisDocument` klasy w projektów na poziomie dokumentu programu Word.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Aby uzyskać więcej informacji na temat pracy z opcjonalnymi parametrami w projektach Visual C# i Visual Basic, zobacz [nazwane i opcjonalne argumenty &#40; K & 35; Przewodnik programowania w języku &#41; ](/dotnet/csharp/programming-guide/classes-and-structs/named-and-optional-arguments) i [następujące parametry opcjonalne &#40; Visual Basic &#41; ](/dotnet/visual-basic/programming-guide/language-features/procedures/optional-parameters).  
  
> [!NOTE]  
>  We wcześniejszych wersjach programu Visual Studio należy podać wartość dla każdego parametru w projektach Visual C#. Dla wygody te projekty obejmują zmiennej globalnej o nazwie `missing` czy można przekazać do opcjonalny parametr Jeśli chcesz użyć wartości domyślnej parametru. Projekty Visual C# dla pakietu Office w Visual Studio nadal zawierają `missing` zmiennej, ale zwykle nie trzeba używać go podczas opracowywania rozwiązań pakietu Office w [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], z wyjątkiem podczas wywoływania metody z opcjonalne **ref** Parametry w `ThisDocument` klasy w projektów na poziomie dokumentu dla programu Word.  
  
## <a name="example-in-excel"></a>Przykład w programie Excel  
 <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A> Metoda ma wiele parametrów opcjonalnych. Można określić wartości dla niektórych parametrów i zaakceptuj wartość domyślną innych osób, jak pokazano w poniższym przykładzie kodu. W tym przykładzie wymaga projekt poziomie dokumentu z arkusza klasę o nazwie `Sheet1`.  
  
 [!code-csharp[Trin_VstrefGeneralExcel#1](../vsto/codesnippet/CSharp/excelworkbook1/Sheet1.cs#1)]
 [!code-vb[Trin_VstrefGeneralExcel#1](../vsto/codesnippet/VisualBasic/excelworkbook1/Sheet1.vb#1)]  
  
## <a name="example-in-word"></a>Przykład w programie Word  
 <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> Metoda ma wiele parametrów opcjonalnych. Można określić wartości dla niektórych parametrów i zaakceptuj wartość domyślną innych osób, jak pokazano w poniższym przykładzie kodu.  
  
 [!code-vb[Trin_VstrefGeneralWord#1](../vsto/codesnippet/VisualBasic/worddocument1/ThisDocument.vb#1)]
 [!code-csharp[Trin_VstrefGeneralWord#1](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#1)]  
  
## <a name="using-optional-parameters-of-methods-in-the-thisdocument-class-in-visual-c-document-level-projects-for-word"></a>Przy użyciu parametrów metod klasy ThisDocument w Visual C# projektów na poziomie dokumentu dla programu Word  
 Model obiektów programu Word zawiera wiele metod o opcjonalne **ref** parametrów, które akceptują <xref:System.Object> wartości. Jednak nie można pominąć opcjonalne **ref** parametrów metod wygenerowany `ThisDocument` klasy w poziomie dokumentu projektach Visual C# dla programu Word. Visual C# umożliwia pominięcie opcjonalne **ref** parametry tylko dla metod interfejsów, nie klasy. Na przykład w poniższym przykładzie kodu nie kompiluje się, ponieważ nie można pominąć opcjonalne **ref** parametry <xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A> metody `ThisDocument` klasy.  
  
 [!code-csharp[Trin_VstrefGeneralWord#3](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#3)]  
  
 Podczas wywoływania metody `ThisDocument` klasy, skorzystaj z następujących wskazówek:  
  
-   Aby zaakceptować domyślną wartość opcjonalna **ref** parametr, przebieg `missing` zmienną do parametru. `missing` Zmiennej automatycznie jest zdefiniowany w projektach Visual C# pakietu Office i jest przypisany do wartości <xref:System.Type.Missing> w kodzie wygenerowanego projektu.  
  
-   Aby określić wartość dla opcjonalny **ref** parametru zadeklarować obiektu, który jest przypisany do wartość, która ma zostać określone, a następnie przekazać obiekt do parametru.  
  
 Poniższy przykład kodu pokazuje sposób wywoływania <xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A> metody, określając wartość *ignoreUppercase* parametru i akceptując wartości domyślne dla innych parametrów.  
  
 [!code-csharp[Trin_VstrefGeneralWord#4](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#4)]  
  
 Aby napisać kod, który umożliwia pominięcie opcjonalne **ref** parametry metody w `ThisDocument` klasy, można również wywołać tę samą metodę w <xref:Microsoft.Office.Interop.Word.Document> obiektu zwróconego przez <xref:Microsoft.Office.Tools.Word.Document.InnerObject%2A> właściwości i pominąć Parametry z tej metody. Można to zrobić, ponieważ <xref:Microsoft.Office.Interop.Word.Document> jest interfejsem, a nie klasy.  
  
 [!code-csharp[Trin_VstrefGeneralWord#5](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#5)]  
  
 Aby uzyskać więcej informacji na temat parametrów typu odwołanie i wartość, zobacz [przekazywanie argumentów według wartości i według odwołania &#40; Visual Basic &#41; ](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference) (w języku Visual Basic) i [przekazywanie parametrów &#40; K & 35; Przewodnik programowania w języku &#41; ](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters).  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie rozwiązań pakietu Office](../vsto/developing-office-solutions.md)   
 [Pisanie kodu dla rozwiązań pakietu Office](../vsto/writing-code-in-office-solutions.md)  
  
  