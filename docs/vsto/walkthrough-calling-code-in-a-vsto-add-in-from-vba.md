---
title: 'Wskazówki: Wywoływanie kodu w dodatku VSTO z kodu VBA'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA [Office development in Visual Studio], calling code in application-level add-ins
- application-level add-ins [Office development in Visual Studio], calling code from other solutions
- Video How tos, Office development in Visual Studio
- calling add-in code
- add-ins [Office development in Visual Studio], calling code from other solutions
- interoperability [Office development in Visual Studio]
- calling code from VBA
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1349facda26418907f039c80c7742d3c456437af
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2018
ms.locfileid: "34845720"
---
# <a name="walkthrough-call-code-in-a-vsto-add-in-from-vba"></a>Wskazówki: Wywoływanie kodu w dodatku VSTO z kodu VBA
  W tym przewodniku pokazano, jak udostępnianie obiektu w dodatku VSTO do innych rozwiązań Microsoft Office, w tym Visual Basic for Applications (VBA) i dodatków COM VSTO.  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
 Mimo że w tym przewodniku zastosowano programu Excel w szczególności, koncepcje dowodzą przewodnika są stosowane do dowolnego dodatku VSTO projektu szablonu dostarczane przez program Visual Studio.  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
-   Definiowanie klasy, które można uwidocznić do innych rozwiązań pakietu Office.  
  
-   Udostępnia klasy do innych rozwiązań pakietu Office.  
  
-   Wywoływanie metody klasy z kodu VBA.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Program Microsoft Excel  
  
## <a name="create-the-vsto-add-in-project"></a>Tworzenie projektów dodatku VSTO  
 Pierwszym krokiem jest utworzenie projektu dodatku VSTO dla programu Excel.  
  
### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt  
  
1.  Tworzenie projektów dodatku VSTO programu Excel o nazwie **ExcelImportData**, za pomocą szablonu projektu dodatku VSTO programu Excel. Aby uzyskać więcej informacji, zobacz [porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Otwiera **ThisAddIn.cs** lub **ThisAddIn.vb** pliku kodu i dodaje **ExcelImportData** projektu do **Eksploratora rozwiązań**.  
  
## <a name="define-a-class-that-you-can-expose-to-other-office-solutions"></a>Definiowanie klasy, która pozwala udostępnić do innych rozwiązań pakietu Office  
 Celem tego przewodnika jest wywołują `ImportData` metody klasy o nazwie `AddInUtilities` w Twojej dodatku VSTO z kodu VBA. Ta metoda zapisuje ciąg w komórce A1 aktywnego arkusza.  
  
 Aby udostępnić `AddInUtilities` klasy do innych rozwiązań pakietu Office, należy klasy publicznej i są widoczne dla modelu COM. Musi również ujawniać [IDispatch](https://msdn.microsoft.com/library/windows/desktop/ms221608.aspx) interfejsu w klasie. Kod w poniższej procedurze pokazano jeden ze sposobów tych wymagań. Aby uzyskać więcej informacji, zobacz [wywoływanie kodu w dodatkach VSTO z innych rozwiązań pakietu Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).  
  
### <a name="to-define-a-class-that-you-can-expose-to-other-office-solutions"></a>Aby zdefiniować klasę, która pozwala udostępnić do innych rozwiązań pakietu Office  
  
1.  Na **projektu** menu, kliknij przycisk **Dodaj klasę**.  
  
2.  W **Dodaj nowy element** okno dialogowe Zmień nazwę nowej klasy do **AddInUtilities**i kliknij przycisk **Dodaj**.  
  
     **AddInUtilities.cs** lub **AddInUtilities.vb** plik zostanie otwarty w edytorze kodu.  
  
3.  Dodaj następujące instrukcje na początku pliku.  
  
     [!code-csharp[Trin_AddInInteropWalkthrough#2](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs#2)]
     [!code-vb[Trin_AddInInteropWalkthrough#2](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb#2)]  
  
4.  Zastąp `AddInUtilities` klasy następującym kodem.  
  
     [!code-csharp[Trin_AddInInteropWalkthrough#3](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs#3)]
     [!code-vb[Trin_AddInInteropWalkthrough#3](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb#3)]  
  
     Ten kod sprawia, że `AddInUtilities` klasy widoczne dla modelu COM, a następnie dodaje `ImportData` metodę do klasy. Aby udostępnić [IDispatch](https://msdn.microsoft.com/library/windows/desktop/ms221608.aspx) interfejsu, `AddInUtilities` klasa ma również <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atrybut który implementuje interfejs, który jest niewidoczny dla modelu COM.  
  
## <a name="expose-the-class-to-other-office-solutions"></a>Udostępnianie klasy do innych rozwiązań pakietu Office  
 Aby udostępnić `AddInUtilities` klasa do innych rozwiązań pakietu Office, Zastąp <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> metody w `ThisAddIn` klasy. W przypadku zastąpienia, zwrócić wystąpienia `AddInUtilities` klasy.  
  
### <a name="to-expose-the-addinutilities-class-to-other-office-solutions"></a>Aby udostępnić klasy AddInUtilities do innych rozwiązań pakietu Office  
  
1.  W **Eksploratora rozwiązań**, rozwiń węzeł **Excel**.  
  
2.  Kliknij prawym przyciskiem myszy **ThisAddIn.cs** lub **ThisAddIn.vb**, a następnie kliknij przycisk **kod widoku**.  
  
3.  Dodaj następujący kod do `ThisAddIn` klasy.  
  
     [!code-csharp[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/ThisAddIn.cs#1)]
     [!code-vb[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/ThisAddIn.vb#1)]  
  
4.  Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.  
  
     Upewnij się, że rozwiązanie kompilacje bez błędów.  
  
## <a name="test-the-vsto-add-in"></a>Testowanie dodatku narzędzi VSTO  
 Można wywołać w `AddInUtilities` klasy z kilkoma różnymi typami rozwiązań pakietu Office. W tym przewodniku użyje kodu z VBA w skoroszycie programu Excel. Aby uzyskać więcej informacji dotyczących innych typów rozwiązań pakietu Office można również użyć, zobacz [wywoływanie kodu w dodatkach VSTO z innych rozwiązań pakietu Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).  
  
### <a name="to-test-your-vsto-add-in"></a>Aby przetestować użytkownika dodatku narzędzi VSTO  
  
1.  Naciśnij klawisz **F5** do uruchomienia projektu.  
  
2.  W programie Excel zapisać aktywnym skoroszycie jako skoroszyt Excel Macro-Enabled (*.xlsm). Zapisz go w dogodnym miejscu, takich jak pulpit.  
  
3.  Na wstążce kliknij **Developer** kartę.  
  
    > [!NOTE]  
    >  Jeśli **Developer** karta nie jest widoczna, należy go najpierw wyświetlić. Aby uzyskać więcej informacji, zobacz [porady: pokazywanie karty dewelopera na wstążce](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  W **kod** kliknij przycisk **Visual Basic**.  
  
     Zostanie otwarty Edytor Visual Basic.  
  
5.  W **projektu** okna, kliknij dwukrotnie **ThisWorkbook**.  
  
     Plik kodowy dla `ThisWorkbook` obiekt zostanie otwarta.  
  
6.  Dodaj następujący kod VBA do pliku kodu. Ten kod pobiera pierwszy obiekt COMAddIn, który reprezentuje **ExcelImportData** dodatku VSTO. Następnie kod używa właściwości obiektu obiektu COMAddIn do wywołania `ImportData` metody.  
  
    ```vb  
    Sub CallVSTOMethod()  
        Dim addIn As COMAddIn  
        Dim automationObject As Object  
        Set addIn = Application.COMAddIns("ExcelImportData")  
        Set automationObject = addIn.Object  
        automationObject.ImportData  
    End Sub  
    ```  
  
7.  Naciśnij klawisz **F5**.  
  
8.  Sprawdź, czy nowy **zaimportowane dane** arkusz został dodany do skoroszytu. Sprawdź również, że A1 komórka zawiera ciąg **to dane**.  
  
9. Zakończ działanie programu Excel.  
  
## <a name="next-steps"></a>Następne kroki  
 Użytkownik może dowiedzieć się więcej o programowanie dodatków VSTO z tych tematów:  
  
-   Użyj `ThisAddIn` klasę, aby zautomatyzować aplikacji hosta i wykonywać inne zadania w projektów dodatku VSTO. Aby uzyskać więcej informacji, zobacz [dodatków VSTO programu](../vsto/programming-vsto-add-ins.md).  
  
-   Tworzenie niestandardowego okienka zadań w dodatku VSTO. Aby uzyskać więcej informacji, zobacz [niestandardowego okienka zadań](../vsto/custom-task-panes.md) i [porady: Dodawanie niestandardowego okienka zadań do aplikacji](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).  
  
-   Dostosowywanie Wstążki w dodatku VSTO. Aby uzyskać więcej informacji, zobacz [Wstążka ― omówienie](../vsto/ribbon-overview.md) i [porady: wprowadzenie do dostosowywania wstążki](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Program dodatków VSTO](../vsto/programming-vsto-add-ins.md)   
 [Wywoływanie kodu w dodatkach VSTO z innych rozwiązań pakietu Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)   
 [Opracowywania rozwiązań pakietu Office](../vsto/developing-office-solutions.md)   
 [Porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Dostosowywanie funkcji interfejsu użytkownika korzystając z rozszerzalności interfejsów](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)  
  
  