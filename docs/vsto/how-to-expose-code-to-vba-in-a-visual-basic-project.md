---
title: "Porady: udostępnianie kodu z VBA w projektach Visual Basic | Dokumentacja firmy Microsoft"
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
- VBA [Office development in Visual Studio], exposing code in document-level customizations
- document-level customizations [Office development in Visual Studio], exposing code
- Visual Basic [Office development in Visual Studio], exposing code to VBA
- exposing code to VBA
- host items [Office development in Visual Studio], exposing code to VBA
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 8d3d007024cdca160c194285da8f0a741100253d
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-expose-code-to-vba-in-a-visual-basic-project"></a>Porady: udostępnianie kodu z VBA w projektach Visual Basic
  Można udostępnianie kodu w [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] projektu Visual Basic dla kodu aplikacji (VBA), jeśli chcesz, aby dwa typy kodu do oddziaływać na siebie.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Proces programu Visual Basic różni się od procesu Visual C#. Aby uzyskać więcej informacji, zobacz [porady: udostępnianie kodu z VBA w Visual C & 35; Projekt](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md).  
  
 Proces jest inny kod w klasie elementu hosta niż dla kodu innych klas:  
  
-   [Udostępnianie kodu w klasie elementu hosta](#HostItemCode)  
  
-   [Udostępnianie kodu, który nie znajduje się w klasie elementu hosta](#NonHostItem)  
  
 ![łącze do wideo](../vsto/media/playvideo.gif "łącze do wideo") dla powiązanych pokaz wideo, zobacz [jak czy I: wywołać VSTO kodu z VBA?](http://go.microsoft.com/fwlink/?LinkId=136757).  
  
##  <a name="HostItemCode"></a>Udostępnianie kodu w klasie elementu hosta  
 Aby włączyć kod VBA wywoła kod Visual Basic w klasie elementu hostów, ustaw **EnableVbaCallers** właściwości elementu hosta do **True**.  
  
 Aby uzyskać wskazówki, który demonstruje sposób ujawnia metody klasy elementu hosta, a następnie wywołać ją z kodu VBA, zobacz [wskazówki: Wywoływanie kodu z VBA w projektach Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md). Aby uzyskać informacje o obiektach hosta, zobacz [elementów hosta i informacje o formantach hosta](../vsto/host-items-and-host-controls-overview.md).  
  
#### <a name="to-expose-code-in-a-host-item-to-vba"></a>Aby udostępnianie kodu w elemencie hosta w VBA  
  
1.  Otwarcia lub utworzenia na poziomie dokumentu [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] projektu, który jest oparty na dokument programu Word, skoroszyt programu Excel lub szablon programu Excel obsługującej makra i zawierający kod VBA.  
  
     Aby uzyskać więcej informacji na temat formatów plików dokumentów, które obsługuje makr zobacz [łączenie VBA i dostosowywanie na poziomie dokumentu](../vsto/combining-vba-and-document-level-customizations.md).  
  
    > [!NOTE]  
    >  Nie można użyć tej funkcji w projektach szablon programu Word.  
  
2.  Upewnij się, że kod VBA w dokumencie może działać bez monitowania użytkownika o włączenie makr. Zaufany kod VBA przez dodanie lokalizacji projektu pakietu Office do listy zaufanych lokalizacji w ustawieniach Centrum zaufania dla programu Word i Excel.  
  
3.  Dodaj właściwości, metody lub zdarzenia, które chcesz udostępnić VBA do jednej z klas elementu hosta w projekcie ani deklarować nowy element członkowski jako **publicznego**. Nazwa klasy jest zależna od aplikacji:  
  
    -   W programie projektu, klasa elementu hosta o nazwie `ThisDocument` domyślnie.  
  
    -   W projekcie programu Excel o nazwie klasy elementu hosta `ThisWorkbook`, `Sheet1`, `Sheet2`, i `Sheet3` domyślnie.  
  
4.  Ustaw **EnableVbaCallers** właściwości elementu hosta do **True**. Ta właściwość jest dostępna w **właściwości** okna, gdy element hosta jest otwarty w projektancie.  
  
     Po ustawieniu tej właściwości, Visual Studio automatycznie ustawia **ReferenceAssemblyFromVbaProject** właściwości **True**.  
  
    > [!NOTE]  
    >  Jeśli skoroszytu lub dokument nie zawiera kodu VBA lub jeśli kod VBA w dokumencie nie jest zaufany do uruchomienia, zostanie wyświetlony komunikat o błędzie w przypadku ustawienia **EnableVbaCallers** właściwości **True**. Jest to spowodowane Visual Studio nie może modyfikować projektu VBA w dokumencie w takiej sytuacji.  
  
5.  Kliknij przycisk **OK** w komunikacie, który jest wyświetlany. Ten komunikat przypomina o tym, że jeśli dodasz kod VBA do skoroszytu lub dokumentu podczas uruchamiasz projektu z [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], kod VBA zostaną utracone podczas następnego skompilować projekt. Jest to spowodowane dokumentu w folderze wyjściowym kompilacji jest zastępowany za każdym razem, gdy skompilować projekt.  
  
     W tym momencie program Visual Studio konfiguruje projekt tak, aby projekt VBA można wywołać w zestawie. Visual Studio dodaje również właściwość o nazwie `CallVSTOAssembly` do `ThisDocument`, `ThisWorkbook`, `Sheet1`, `Sheet2`, lub `Sheet3` modułu w projekcie języka VBA. Ta właściwość umożliwia dostęp do publicznych elementów członkowskich klasy, która narażonych na VBA.  
  
6.  Skompiluj projekt.  
  
##  <a name="NonHostItem"></a>Udostępnianie kodu, który nie znajduje się w klasie elementu hosta  
 Aby włączyć kod VBA wywoła kod Visual Basic, który nie znajduje się w klasie elementu hosta, należy zmodyfikować kod, aby nie jest widoczna w VBA.  
  
#### <a name="to-expose-code-that-is-not-in-a-host-item-class-to-vba"></a>Aby udostępnianie kodu, który nie znajduje się w klasie elementu hosta w VBA  
  
1.  Otwarcia lub utworzenia na poziomie dokumentu [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] projektu, który jest oparty na dokument programu Word, skoroszyt programu Excel lub szablon programu Excel obsługującej makra i zawierający kod VBA.  
  
     Aby uzyskać więcej informacji na temat formatów plików dokumentów, które obsługuje makr zobacz [łączenie VBA i dostosowywanie na poziomie dokumentu](../vsto/combining-vba-and-document-level-customizations.md).  
  
    > [!NOTE]  
    >  Nie można użyć tej funkcji w projektach szablon programu Word.  
  
2.  Upewnij się, że kod VBA w dokumencie może działać bez monitowania użytkownika o włączenie makr. Zaufany kod VBA przez dodanie lokalizacji projektu pakietu Office do listy zaufanych lokalizacji w ustawieniach Centrum zaufania dla programu Word i Excel.  
  
3.  Dodaj element członkowski, który chcesz udostępnić VBA do publicznej klasy w projekcie ani deklarować nowy element członkowski jako **publicznego**.  
  
4.  Zastosuj następujące <xref:System.Runtime.InteropServices.ComVisibleAttribute> i <xref:Microsoft.VisualBasic.ComClassAttribute> atrybuty do klasy, która wyświetlasz VBA. Te atrybuty uwidaczniania klasy VBA.  
  
    ```vb  
    <Microsoft.VisualBasic.ComClass()> _  
    <System.Runtime.InteropServices.ComVisibleAttribute(True)> _  
    ```  
  
5.  Zastąpienie **GetAutomationObject** metody klasy elementu hosta w projekcie można zwrócić wystąpienia klasy, która wyświetlasz VBA. Poniższy przykład kodu zakłada wyświetlasz klasę o nazwie `DocumentUtilities` VBA.  
  
    ```vb  
    Protected Overrides Function GetAutomationObject() As Object  
        Return New DocumentUtilities()  
    End Function  
    ```  
  
6.  Otwórz dokument (dla programu Word) lub projektanta arkusza (dla programu Excel) w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
7.  W **właściwości** wybierz **ReferenceAssemblyFromVbaProject** właściwości i zmień wartość na **True**.  
  
    > [!NOTE]  
    >  Jeśli skoroszytu lub dokument nie zawiera kodu VBA lub jeśli kod VBA w dokumencie nie jest zaufany do uruchomienia, zostanie wyświetlony komunikat o błędzie w przypadku ustawienia **ReferenceAssemblyFromVbaProject** właściwości **wartość True** . Jest to spowodowane Visual Studio nie może modyfikować projektu VBA w dokumencie w takiej sytuacji.  
  
8.  Kliknij przycisk **OK** w komunikacie, który jest wyświetlany. Ten komunikat przypomina o tym, że jeśli dodasz kod VBA do skoroszytu lub dokumentu podczas uruchamiasz projektu z [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], kod VBA zostaną utracone podczas następnego skompilować projekt. Jest to spowodowane dokumentu w folderze wyjściowym kompilacji jest zastępowany za każdym razem, gdy skompilować projekt.  
  
     W tym momencie program Visual Studio konfiguruje projekt tak, aby projekt VBA można wywołać w zestawie. Visual Studio również dodaje metodę o nazwie `GetManagedClass` do projektu języka VBA. Tę metodę można wywołać z dowolnego miejsca w projekcie VBA dostępu do tej klasy, która narażonych na VBA.  
  
9. Skompiluj projekt.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)   
 [Łączenie VBA i dostosowywanie na poziomie dokumentu](../vsto/combining-vba-and-document-level-customizations.md)   
 [Wskazówki: Wywoływanie kodu z VBA w projektach Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)   
 [Porady: udostępnianie kodu z VBA w Visual C & 35; Projekt](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)  
  
  