---
title: 'Porady: udostępnianie kodu z VBA w projektach Visual C#'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual C# [Office development in Visual Studio], exposing code to VBA
- VBA [Office development in Visual Studio], exposing code in document-level customizations
- document-level customizations [Office development in Visual Studio], exposing code
- exposing code to VBA
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 36bdcd7360099818ac8510d9eab87d6d3dc0f0fc
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257254"
---
# <a name="how-to-expose-code-to-vba-in-a-visual-c-project"></a>Porady: udostępnianie kodu z VBA w projektach Visual C#
  Można udostępnianie kodu w projektach Visual C# na język Visual Basic dla kodu aplikacji (VBA), jeśli chcesz, aby dwa typy kodu do oddziaływać na siebie.  
  
 Proces Visual C# różni się od procesu Visual Basic. Aby uzyskać więcej informacji, zobacz [porady: udostępnianie kodu z VBA w projektach Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="expose-code-in-a-visual-c-project"></a>Udostępnianie kodu w projektach Visual C#  
 Aby włączyć kod VBA wywoływanie kodu w projektach Visual C#, należy zmodyfikować kod, tak aby widoczne dla modelu COM, a następnie ustaw **ReferenceAssemblyFromVbaProject** właściwości **True** w projektancie.  
  
 Aby uzyskać wskazówki, który demonstruje sposób wywołania metody w projektach Visual C# z kodu VBA, zobacz [wskazówki: Wywoływanie kodu z VBA w Visual C&#35; projektu](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md).  
  
### <a name="to-expose-code-in-a-visual-c-project-to-vba"></a>Aby udostępnianie kodu w projektach Visual C# w VBA  
  
1.  Otwórz lub Utwórz projekt poziomie dokumentu, który jest oparty na dokument programu Word, skoroszyt programu Excel lub szablon programu Excel obsługującej makra i zawierający kod VBA.  
  
     Aby uzyskać więcej informacji na temat formatów plików dokumentów, które obsługuje makr zobacz [łączenie VBA i dostosowywanie na poziomie dokumentu](../vsto/combining-vba-and-document-level-customizations.md).  
  
    > [!NOTE]  
    >  Nie można użyć tej funkcji w projektach szablon programu Word.  
  
2.  Upewnij się, że kod VBA w dokumencie może działać bez monitowania użytkownika o włączenie makr. Zaufany kod VBA przez dodanie lokalizacji projektu pakietu Office do listy zaufanych lokalizacji w ustawieniach Centrum zaufania dla programu Word i Excel.  
  
3.  Dodaj element członkowski, który chcesz udostępnić VBA do publicznej klasy w projekcie ani deklarować nowy element członkowski jako **publicznego**.  
  
4.  Zastosuj następujące <xref:System.Runtime.InteropServices.ComVisibleAttribute> i <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atrybuty do klasy, która wyświetlasz VBA. Te atrybuty uwidaczniania klasy COM, ale bez generowania interfejsu klasy.  
  
    ```csharp  
    [System.Runtime.InteropServices.ComVisible(true)]  
    [System.Runtime.InteropServices.ClassInterface(  
        System.Runtime.InteropServices.ClassInterfaceType.None)]  
    ```  
  
5.  Zastąpienie **GetAutomationObject** metody klasy elementu hosta w projekcie można zwrócić wystąpienia klasy, która wyświetlasz VBA:  
  
    -   Jeśli wyświetlasz klasy elementu obsługującej VBA zastępują **GetAutomationObject** metodę, która należy do tej klasy, a następnie wróć bieżące wystąpienie klasy.  
  
        ```csharp  
        protected override object GetAutomationObject()  
        {  
            return this;  
        }  
        ```  
  
    -   Jeśli wyświetlasz klasę, która nie jest elementem hosta VBA zastępują **GetAutomationObject** metoda dowolnego hosta elementu w projekcie i zwrócić wystąpienia klasy elementu-host. Na przykład następujący kod przyjęto założenie, że wyświetlasz klasę o nazwie `DocumentUtilities` VBA.  
  
        ```csharp  
        protected override object GetAutomationObject()  
        {  
            return new DocumentUtilities();  
        }  
        ```  
  
     Aby uzyskać informacje o obiektach hosta, zobacz [elementów, a informacje o formantach](../vsto/host-items-and-host-controls-overview.md).  
  
6.  Wyodrębnij interfejs z klasy, która wyświetlasz VBA. W **wyodrębniania interfejsu** oknie dialogowym Wybierz publiczne elementy członkowskie, które chcesz uwzględnić w deklaracji interfejsu. Aby uzyskać więcej informacji, zobacz [wyodrębniania interfejsu refaktoryzacji](../ide/reference/extract-interface.md).
  
7.  Dodaj **publicznego** — słowo kluczowe do deklaracji interfejsu.  
  
8.  Udostępnienie interfejs dla modelu COM przez dodanie poniższego <xref:System.Runtime.InteropServices.ComVisibleAttribute> do interfejsu.  
  
    ```csharp  
    [System.Runtime.InteropServices.ComVisible(true)]  
    ```  
  
9. Otwórz dokument (dla programu Word) lub arkusz (dla programu Excel) w projektancie w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
10. W **właściwości** wybierz **ReferenceAssemblyFromVbaProject** właściwości i zmień wartość na **True**.  
  
    > [!NOTE]  
    >  Jeśli skoroszytu lub dokument nie zawiera kodu VBA lub jeśli kod VBA w dokumencie nie jest zaufany do uruchomienia, zostanie wyświetlony komunikat o błędzie w przypadku ustawienia **ReferenceAssemblyFromVbaProject** właściwości **True**. Jest to spowodowane Visual Studio nie może modyfikować projektu VBA w dokumencie w takiej sytuacji.  
  
11. Kliknij przycisk **OK** w komunikacie, który jest wyświetlany. Ten komunikat przypomina o tym, że jeśli dodasz VBA kodu do skoroszytu lub dokumentu podczas uruchamiania projektu z [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], kod VBA zostaną utracone przy następnym uruchomieniu skompilować projekt. Jest to spowodowane dokumentu w kompilacji output się, że folder zostanie zastąpiony zawsze skompilować projekt.  
  
     W tym momencie program Visual Studio konfiguruje projekt tak, aby projekt VBA można wywołać w zestawie. Visual Studio również dodaje metodę o nazwie `GetManagedClass` do projektu języka VBA. Tę metodę można wywołać z dowolnego miejsca w projekcie VBA dostępu do tej klasy, która narażonych na VBA.  
  
12. Skompiluj projekt.  
  
## <a name="see-also"></a>Zobacz także  
 [Porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)   
 [Łączenie VBA i dostosowywanie na poziomie dokumentu](../vsto/combining-vba-and-document-level-customizations.md)   
 [Wskazówki: Wywoływanie kodu z VBA w Visual C&#35; projektu](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)   
 [Porady: udostępnianie kodu z VBA w projektach Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)  
  
  