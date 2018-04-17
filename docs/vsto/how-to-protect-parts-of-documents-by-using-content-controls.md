---
title: 'Porady: ochrona części dokumentów za pomocą formantów zawartości | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- restricted permissions [Office development in Visual Studio]
- partial document protection [Office development in Visual Studio]
- content controls [Office development in Visual Studio], protecting documents
- Word [Office development in Visual Studio], partial document protection
- document protection [Office development in Visual Studio]
- Word [Office development in Visual Studio], restricted permissions
- GroupContentControl
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0a72603f71395bbbf8e167b6a2361f7d8b2a30a6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-protect-parts-of-documents-by-using-content-controls"></a>Porady: ochrona części dokumentów za pomocą formantów zawartości
  W przypadku ochrony części dokumentu, można uniemożliwić użytkownikom zmienianie lub usuwanie zawartości w tej części dokumentu. Istnieje kilka sposobów części dokumentu Microsoft Office Word można chronić za pomocą formantów zawartości:  
  
-   Można chronić zawartość formantu.  
  
-   Można chronić części dokumentu, który nie jest w formancie zawartości.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
##  <a name="EditDeleteControl"></a> Ochrona zawartości formantu  
 Można uniemożliwić użytkownikom edytowanie lub usuwanie zawartości formantu przez ustawienie właściwości formantu w projektach na poziomie dokumentu w czasie projektowania lub w czasie wykonywania.  
  
 Umożliwia również ochronę zawartości formanty dodane do dokumentu w czasie wykonywania za pomocą projektów dodatku VSTO. Aby uzyskać więcej informacji, zobacz [porady: dodawanie formantów zawartości do dokumentów programu Word](../vsto/how-to-add-content-controls-to-word-documents.md).  
  
#### <a name="to-protect-a-content-control-at-design-time"></a>Aby chronić zawartość formantu w czasie projektowania  
  
1.  W dokumencie, który znajduje się w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektanta, wybierz formant zawartości, który chcesz chronić.  
  
2.  W **właściwości** okno, ustawić jedną lub obie następujące właściwości:  
  
    -   Aby uniemożliwić użytkownikom edytowanie formantu, należy ustawić **LockContents** do **True**.  
  
    -   Aby zapobiec usunięciu formantu, należy ustawić **LockContentControl** do **True**.  
  
3.  Kliknij przycisk **OK**.  
  
#### <a name="to-protect-a-content-control-at-run-time"></a>Aby chronić zawartość formantu w czasie wykonywania  
  
1.  Ustaw `LockContents` właściwości zawartości formantu **true** aby uniemożliwić użytkownikom edytowanie formantu i ustawić `LockContentControl` właściwości **true** aby uniemożliwić użytkownikom usunięcie formantu.  
  
     Poniższy przykład kodu pokazuje, za pomocą <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContents%2A> i <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContentControl%2A> właściwości dwóch różnych <xref:Microsoft.Office.Tools.Word.RichTextContentControl> obiektów w projektach na poziomie dokumentu. Aby uruchomić ten kod, Dodaj kod, aby `ThisDocument` klasy w projekcie i wywołanie `AddProtectedContentControls` metody z `ThisDocument_Startup` obsługi zdarzeń.  
  
     [!code-csharp[Trin_ContentControlHowToProtect#2](../vsto/codesnippet/CSharp/Trin_ContentControlHowToProtect/ThisDocument.cs#2)]
     [!code-vb[Trin_ContentControlHowToProtect#2](../vsto/codesnippet/VisualBasic/Trin_ContentControlHowToProtect/ThisDocument.vb#2)]  
  
     Poniższy przykład kodu pokazuje, za pomocą <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContents%2A> i <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContentControl%2A> właściwości dwóch różnych <xref:Microsoft.Office.Tools.Word.RichTextContentControl> obiektów w projekcie dodatku VSTO. Aby uruchomić ten kod, Dodaj kod, aby `ThisAddIn` klasy w projekcie i wywołanie `AddProtectedContentControls` metody z `ThisAddIn_Startup` obsługi zdarzeń.  
  
     [!code-vb[Trin_WordAddInDynamicControls#14](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#14)]
     [!code-csharp[Trin_WordAddInDynamicControls#14](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#14)]  
  
## <a name="protecting-a-part-of-a-document-that-is-not-in-a-content-control"></a>Ochrona części dokumentu, który nie jest w formancie zawartości  
 Użytkownik może uniemożliwić użytkownikom zmianę obszar dokumentu umieszczenie w obszarze <xref:Microsoft.Office.Tools.Word.GroupContentControl>. Jest to przydatne w następujących scenariuszach:  
  
-   Chcesz chronić obszar, w którym nie zawiera formanty zawartości.  
  
-   Aby chronić obszar, w którym już zawiera formanty zawartości, ale tekst lub innych elementów, które mają być chronione nie są w formantach zawartości.  
  
> [!NOTE]  
>  W przypadku utworzenia <xref:Microsoft.Office.Tools.Word.GroupContentControl> zawiera osadzony formantów zawartości, osadzonych formantów zawartości nie są automatycznie chronione. Aby uniemożliwić użytkownikom edytowanie osadzonego formantu zawartości, należy użyć **LockContents** właściwości formantu.  
  
#### <a name="to-protect-an-area-of-a-document-at-design-time"></a>Aby chronić obszar dokumentu w czasie projektowania  
  
1.  W dokumencie, który znajduje się w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektanta, wybierz obszar, który chcesz chronić.  
  
2.  Na wstążce kliknij **Developer** kartę.  
  
    > [!NOTE]  
    >  Jeśli **Developer** karta nie jest widoczna, należy go najpierw wyświetlić. Aby uzyskać więcej informacji, zobacz [porady: pokazywanie karty dewelopera na wstążce](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
3.  W **formanty** kliknij przycisk **grupy** przycisku rozwijanego, a następnie kliknij przycisk **grupy**.  
  
     A <xref:Microsoft.Office.Tools.Word.GroupContentControl> zawierający chronionej region jest automatycznie generowany w `ThisDocument` klasy w projekcie. Obramowanie reprezentujący kontrolkę grupy jest widoczny w czasie projektowania, ale nie będzie widoczny obramowania w czasie wykonywania.  
  
#### <a name="to-protect-an-area-of-a-document-at-run-time"></a>Aby chronić obszar dokumentu w czasie wykonywania  
  
1.  Programowo wybierz obszar, który chcesz chronić, a następnie wywołać <xref:Microsoft.Office.Tools.Word.ControlCollection.AddGroupContentControl%2A> metodę w celu utworzenia <xref:Microsoft.Office.Tools.Word.GroupContentControl>.  
  
     Poniższy przykład kodu dla projektu poziomie dokumentu dodaje tekst akapitu w dokumencie wybiera pierwszym akapicie, a następnie tworzy <xref:Microsoft.Office.Tools.Word.GroupContentControl>. Aby uruchomić ten kod, Dodaj kod, aby `ThisDocument` klasy w projekcie i wywołanie `ProtectFirstParagraph` metody z `ThisDocument_Startup` obsługi zdarzeń.  
  
     [!code-csharp[Trin_ContentControlHowToProtect#1](../vsto/codesnippet/CSharp/Trin_ContentControlHowToProtect/ThisDocument.cs#1)]
     [!code-vb[Trin_ContentControlHowToProtect#1](../vsto/codesnippet/VisualBasic/Trin_ContentControlHowToProtect/ThisDocument.vb#1)]  
  
     Poniższy przykład kodu dla projektów dodatku VSTO dodaje tekst akapitu w aktywnym dokumencie wybiera pierwszym akapicie, a następnie tworzy <xref:Microsoft.Office.Tools.Word.GroupContentControl>. Aby uruchomić ten kod, Dodaj kod, aby `ThisAddIn` klasy w projekcie i wywołanie `ProtectFirstParagraph` metody z `ThisAddIn_Startup` obsługi zdarzeń.  
  
     [!code-vb[Trin_WordAddInDynamicControls#15](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#15)]
     [!code-csharp[Trin_WordAddInDynamicControls#15](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#15)]  
  
## <a name="see-also"></a>Zobacz też  
 [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)   
 [Formanty zawartości](../vsto/content-controls.md)   
 [Porady: dodawanie formantów zawartości do dokumentów programu Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Obiekty hosta i informacje o formantach hosta](../vsto/host-items-and-host-controls-overview.md)   
 [Ograniczenia programowe elementów hosta i formantów hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)  
   