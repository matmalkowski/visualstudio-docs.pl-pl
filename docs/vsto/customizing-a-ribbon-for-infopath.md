---
title: Dostosowywanie wstążki do InfoPath | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- InfoPath [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], InfoPath
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a3e5121285f66059a898ce64fc4107903f371485
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="customizing-a-ribbon-for-infopath"></a>Dostosowywanie Wstążki do InfoPath
  Podczas dostosowywania wstążki w programie Microsoft Office InfoPath należy rozważyć, gdy Twoje niestandardowa Wstążka będą wyświetlane w aplikacji. [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)] może wyświetlać wstążki w następujących trzech typów InfoPath aplikacji systemu windows:  
  
-   W przypadku systemu Windows, wyświetlające szablonu formularza, który jest otwarty w trybie projektowania.  
  
-   W przypadku systemu Windows, wyświetlające formularz, który jest oparty na szablonie formularza.  
  
-   Okno podglądu wydruku.  
  
 **Dotyczy:** informacje przedstawione w tym temacie dotyczą projektów dodatku VSTO dla programu InfoPath 2010. Aby uzyskać więcej informacji, zobacz [dostępne funkcje uporządkowane według aplikacji pakietu Office i typu projektu](../vsto/features-available-by-office-application-and-project-type.md).  
  
 Użytkownicy i projektantów Otwórz formularz w trybie projektowania, aby zmodyfikować wygląd i układ szablonu. Użytkownicy otworzyć formularzy opartych w szablonie formularza w celu dodania zawartości.  
  
 Okno podglądu wydruku umożliwia projektantów i użytkowników przed ich drukowania w wersji preview na stronach formularza lub szablonem.  
  
> [!NOTE]  
>  **Dodatków** karta nie jest wyświetlana w oknie Podgląd wydruku. Jeśli chcesz kart niestandardowych pojawią się w oknie Podgląd wydruku, upewnij się, że **OfficeId** nie ustawiono właściwości karty **TabAddIns**.  
  
 Należy określić typ wstążki każdego okien użytkownika wstążki pojawią się.  
  
## <a name="specifying-the-ribbon-type-in-the-ribbon-designer"></a>Określanie typu wstążki w Projektancie wstążki  
 Jeśli używasz **wstążki (projektanta wizualnego)** element, kliknij przycisk **RibbonType** właściwości wstążki w **właściwości** okna, a następnie ustaw identyfikator wstążki opisane w poniższej tabeli.  
  
|Identyfikator wstążki|Okno, w którym wstążce pojawi się po uruchomieniu projektu|  
|---------------|---------------------------------------------------------------------|  
|**Microsoft.InfoPath.Designer**|W przypadku systemu Windows, wyświetlające szablonu formularza, który jest otwarty w trybie projektowania.|  
|**Microsoft.InfoPath.Editor**|W przypadku systemu Windows, wyświetlające formularz, który jest oparty na szablonie formularza.|  
|**Microsoft.InfoPath.PrintPreview**|Okno podglądu wydruku.|  
  
 Można dodać więcej niż jeden wstążki do projektu. Jeśli kilka wstążce udostępniać identyfikator wstążki, Zastąp metodę CreateRibbonExtensibilityObject w `ThisAddin` klasy z projektem, aby określić, które wstążki do wyświetlenia w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [Wstążka ― omówienie](../vsto/ribbon-overview.md).  
  
## <a name="specifying-the-ribbon-type-by-using-ribbon-xml"></a>Określanie typu wstążki za pomocą XML wstążki  
 Jeśli używasz **wstążki (XML)** element, należy sprawdzić wartość *ribbonID* parametru w <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> — metoda i przywracać odpowiednie wstążki.  
  
 <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> Metody jest generowana automatycznie przez program Visual Studio w pliku kodu wstążki. *RibbonID* parametru jest ciągiem, który określa typ InfoPath okna, które jest otwierane.  
  
 Poniższy przykład kodu pokazuje sposób wyświetlania niestandardowa Wstążka tylko w oknie, który wyświetla szablon formularza w trybie projektowania. Na Wstążce, aby wyświetlić została określona w `GetResourceText()` metodę, która jest generowana w klasie wstążki. Aby uzyskać więcej informacji o klasie wstążki, zobacz [kodu XML wstążki](../vsto/ribbon-xml.md).  
  
 [!code-csharp[Trin_RibbonInfoPathBasic#1](../vsto/codesnippet/CSharp/myinfopathproject/ribbon.cs#1)]
 [!code-vb[Trin_RibbonInfoPathBasic#1](../vsto/codesnippet/VisualBasic/myinfopathproject/ribbon.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Uzyskiwanie dostępu do wstążki w czasie wykonywania](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Wstążka ― omówienie](../vsto/ribbon-overview.md)   
 [Projektant wstążki](../vsto/ribbon-designer.md)   
 [XML — wstążka](../vsto/ribbon-xml.md)  
  
  