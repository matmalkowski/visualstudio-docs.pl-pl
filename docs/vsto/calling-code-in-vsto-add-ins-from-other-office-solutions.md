---
title: Wywoływanie kodu w dodatkach VSTO z innych rozwiązań pakietu Office | Dokumentacja firmy Microsoft
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
- calling add-in code
- add-ins [Office development in Visual Studio], calling code from other solutions
- interoperability [Office development in Visual Studio]
- calling code from VBA
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1f256cf8fd0b5c89a0d9e6a9733680aac9257cd4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="calling-code-in-vsto-add-ins-from-other-office-solutions"></a>Wywoływanie kodu w dodatkach VSTO z innych rozwiązań pakietu Office
  Obiekt mogą uwidaczniać w Twojej dodatku VSTO do innych rozwiązań, łącznie z innych rozwiązań Microsoft Office. Jest to przydatne, jeśli dodatek VSTO udostępnia usługi, który chcesz włączyć innych rozwiązań do użycia. Na przykład jeśli masz dodatku VSTO dla programu Microsoft Office Excel wykonuje obliczenia na danych finansowych z usługi sieci Web, inne rozwiązania można wykonać tych obliczeń przez wywołanie dodatku VSTO programu Excel w czasie wykonywania.  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
 W tym procesie istnieją dwa podstawowe kroki:  
  
-   W dodatku programu VSTO ujawnia obiekt do innych rozwiązań.  
  
-   W inne rozwiązanie dostępu do obiektu, udostępnione przez użytkownika dodatku VSTO i wywołanie elementów członkowskich obiektu.  
  
## <a name="types-of-solutions-that-can-call-code-in-an-add-in"></a>Typy rozwiązań, które może wywoływać kodu w dodatkach  
 Można udostępnić obiektu w dodatku VSTO dla następujących typów rozwiązań:  
  
-   Kod Visual Basic for Applications (VBA) w dokumencie, który jest ładowany w tym samym procesie aplikacji jako użytkownika dodatku VSTO.  
  
-   Dostosowywanie na poziomie dokumentu załadowanych do tego samego procesu aplikacji, co Twoje dodatku VSTO.  
  
-   Inne VSTO dodatki utworzone przy użyciu szablonów projektu pakietu Office w Visual Studio.  
  
-   Dodatków COM VSTO (to znaczy VSTO dodatki implementujących <xref:Extensibility.IDTExtensibility2> interfejsu bezpośrednio).  
  
-   Dowolnego rozwiązania, które działa w ramach innego procesu niż dodatek VSTO (tych typów rozwiązań także są nazywane *klientów poza procesem*). Obejmują one aplikacje, które automatyzują aplikacji pakietu Office, takich jak aplikacji formularzy systemu Windows lub konsoli i dodatków VSTO, które są ładowane w ramach innego procesu.  
  
## <a name="exposing-objects-to-other-solutions"></a>Udostępnianie obiektów do innych rozwiązań  
 Do udostępnienia obiektu w Twojej dodatku VSTO z innymi rozwiązaniami, wykonaj następujące czynności w dodatku VSTO programu:  
  
1.  Definiowanie klasy, która powinna być ujawniona do innych rozwiązań.  
  
2.  Zastąpienie <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> metoda `ThisAddIn` klasy. Zwraca wystąpienie klasy, który chcesz udostępnić do innych rozwiązań.  
  
### <a name="defining-the-class-you-want-to-expose-to-other-solutions"></a>Definiowanie klasy, którą chcesz uwidocznić do innych rozwiązań  
 Co najmniej klasy chcesz udostępnić muszą być publiczne, musi on mieć <xref:System.Runtime.InteropServices.ComVisibleAttribute> ustawić atrybutu **true**, i musi uwidaczniać jej [IDispatch](https://msdn.microsoft.com/library/windows/desktop/ms221608.aspx) interfejsu.  
  
 Zalecanym sposobem ujawnia [IDispatch](https://msdn.microsoft.com/library/windows/desktop/ms221608.aspx) interfejs ma wykonać następujące czynności:  
  
1.  Zdefiniuj interfejs, który deklaruje elementów członkowskich, które chcesz udostępnić do innych rozwiązań. Ten interfejs można zdefiniować w projekcie dodatku VSTO. Można jednak zdefiniować ten interfejs w projekcie biblioteki osobnej klasy, jeśli chcesz udostępnić klasy do rozwiązań z systemem innym niż VBA tak, aby rozwiązania, które wywołać dodatek VSTO może odwoływać się interfejs bez odwołania do projektu dodatków narzędzi VSTO.  
  
2.  Zastosuj <xref:System.Runtime.InteropServices.ComVisibleAttribute> atrybutu do tego interfejsu i ustaw ten atrybut **true**.  
  
3.  Modyfikowanie klasy do zaimplementowania tego interfejsu.  
  
4.  Zastosuj <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atrybutu do klasy, a wartość tego atrybutu None wartość <xref:System.Runtime.InteropServices.ClassInterfaceType> wyliczenia.  
  
5.  Jeśli chcesz udostępnić klasy klientom poza procesem, konieczne może wykonać następujące czynności:  
  
    -   Pochodzi z klasy <xref:System.Runtime.InteropServices.StandardOleMarshalObject>. Aby uzyskać więcej informacji, zobacz [klasy udostępnianie klientom poza procesem](#outofproc).  
  
    -   Ustaw **Zarejestruj dla międzyoperacyjności z modelem COM** właściwości w projekcie, w którym zdefiniować interfejs. Jest to konieczne tylko wtedy, gdy chcesz umożliwić klientom używanie wczesne powiązania do wywołania w dodatku VSTO.  
  
 Poniższy przykład kodu pokazuje `AddInUtilities` klasy z `ImportData` metodę, która może być wywoływany przez inne rozwiązania. Aby wyświetlić ten kod w kontekście większych wskazówki, zobacz [wskazówki: Wywoływanie kodu w dodatku VSTO z kodu VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).  
  
 [!code-csharp[Trin_AddInInteropWalkthrough#3](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs#3)]
 [!code-vb[Trin_AddInInteropWalkthrough#3](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb#3)]  
  
### <a name="exposing-classes-to-vba"></a>Udostępnianie klas w VBA  
 Po wykonaniu powyższych kroków kod VBA można wywołać tylko z metod, które można zadeklarować w interfejsie. Kod VBA nie można wywołać inne metody w klasie, w tym metod, które klasy uzyskuje z klas podstawowych, takich jak <xref:System.Object>.  
  
 Można również udostępnić [IDispatch](https://msdn.microsoft.com/library/windows/desktop/ms221608.aspx) interfejsu przez ustawienie <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atrybut na wartość AutoDispatch lub AutoDual <xref:System.Runtime.InteropServices.ClassInterfaceType> wyliczenia. Jeśli to zrobisz, nie trzeba zadeklarować metody w oddzielnych interfejsu. Jednak kod VBA może wywołać wszystkie publiczne i niestatycznej metody w klasie, w tym metody uzyskane z klas podstawowych, takich jak <xref:System.Object>. Ponadto poza procesem klientów, którzy używają wczesne powiązania nie można wywołać klasy.  
  
###  <a name="outofproc"></a> Udostępnianie klasy klientom poza procesem.  
 Jeśli chcesz udostępnić klasę w Twojej dodatku VSTO dla klientów poza procesem, powinien pochodzić z klasy <xref:System.Runtime.InteropServices.StandardOleMarshalObject> aby upewnić się, że klientów poza procesem można wywołać obiektu dostępnego dodatku VSTO. W przeciwnym razie próbuje pobrać wystąpienia obiektu uwidocznione w kliencie poza procesem mogą nieoczekiwanie zakończyć się niepowodzeniem.  
  
 Jest to spowodowane wszystkie wywołania object model aplikacji pakietu Office, muszą być wprowadzane w głównym wątku interfejsu użytkownika, ale wywołania z klienta poza procesem obiektu pojawią się w dowolnego wątku RPC (zdalne wywołania procedur). Mechanizm kierowania modelu COM w programie .NET Framework nie przełączy wątków, a zamiast tego będzie podejmować próby zorganizowania wywołania obiektu na wątek przychodzący RPC zamiast głównego wątku interfejsu użytkownika. Jeśli obiekt jest wystąpieniem klasy, która jest pochodną <xref:System.Runtime.InteropServices.StandardOleMarshalObject>, przychodzące wywołania obiektu są automatycznie przekazywane do wątku, której został utworzony obiekt narażonych, będzie głównym wątku interfejsu użytkownika w aplikacji hosta.  
  
 Aby uzyskać więcej informacji o używaniu wątków w rozwiązaniach pakietu Office, zobacz [Obsługa wątkowości w pakiecie Office](../vsto/threading-support-in-office.md).  
  
### <a name="overriding-the-requestcomaddinautomationservice-method"></a>Zastąpienie metody RequestComAddInAutomationService  
 W poniższym przykładzie pokazano, jak zastąpić <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> w `ThisAddIn` klasy w Twojej dodatku VSTO. W tym przykładzie założono, że zdefiniowano klasę o nazwie `AddInUtilities` interesujące dla innych rozwiązań. Aby wyświetlić ten kod w kontekście większych wskazówki, zobacz [wskazówki: Wywoływanie kodu w dodatku VSTO z kodu VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).  
  
 [!code-csharp[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/ThisAddIn.cs#1)]
 [!code-vb[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/ThisAddIn.vb#1)]  
  
 Gdy dodatek VSTO został załadowany, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] wywołania <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> metody. Środowisko uruchomieniowe przypisuje zwrócony obiekt do <xref:Microsoft.Office.Core.COMAddIn.Object%2A> właściwość <xref:Microsoft.Office.Core.COMAddIn> obiekt, który reprezentuje użytkownika dodatku VSTO. To <xref:Microsoft.Office.Core.COMAddIn> obiekt jest dostępny w innych rozwiązań pakietu Office i rozwiązań, które automatyzują pakietu Office.  
  
## <a name="accessing-objects-from-other-solutions"></a>Uzyskiwanie dostępu do obiektów z innych rozwiązań  
 Aby wywołać obiekt uwidocznione w dodatku VSTO programu, wykonaj następujące czynności w rozwiązaniu klienta:  
  
1.  Pobierz <xref:Microsoft.Office.Core.COMAddIn> obiekt, który reprezentuje dostępnego dodatku VSTO. Klienci mogą uzyskać dostęp do wszystkich dostępnych dodatków narzędzi VSTO przy użyciu właściwości Application.COMAddIns w modelu obiektu hosta aplikacji pakietu Office.  
  
2.  Dostęp <xref:Microsoft.Office.Core.COMAddIn.Object%2A> właściwość <xref:Microsoft.Office.Core.COMAddIn> obiektu. Ta właściwość zwraca obiekt narażonych z dodatku VSTO.  
  
3.  Wywołanie członkami narażonych obiektu.  
  
 Sposób użycia wartość zwracaną <xref:Microsoft.Office.Core.COMAddIn.Object%2A> właściwości jest różna dla VBA i klientami z systemem innym niż VBA. Dla klientów poza procesem dodatkowy kod jest niezbędne uniknąć możliwych wyścigu.  
  
### <a name="accessing-objects-from-vba-solutions"></a>Uzyskiwanie dostępu do obiektów z rozwiązań VBA  
 Poniższy przykład kodu pokazuje, jak używać języka VBA do wywołania metody, która jest udostępniana przez dodatku VSTO. To makro VBA wywołuje metodę o nazwie `ImportData` zdefiniowanego w dodatku VSTO o nazwie **ExcelImportData**. Aby wyświetlić ten kod w kontekście większych wskazówki, zobacz [wskazówki: Wywoływanie kodu w dodatku VSTO z kodu VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).  
  
```  
Sub CallVSTOMethod()  
    Dim addIn As COMAddIn  
    Dim automationObject As Object  
    Set addIn = Application.COMAddIns("ExcelImportData")  
    Set automationObject = addIn.Object  
    automationObject.ImportData  
End Sub  
```  
  
### <a name="accessing-objects-from-non-vba-solutions"></a>Uzyskiwanie dostępu do obiektów z rozwiązań z systemem innym niż VBA  
 W rozwiązaniu VBA nie można rzutować <xref:Microsoft.Office.Core.COMAddIn.Object%2A> wartość właściwości do interfejsu ją implementuje, i wywoływać metody narażonych na obiekt interfejsu. Poniższy przykład kodu pokazuje sposób wywoływania `ImportData` metodę z innej VSTO dodatku, który został utworzony przy użyciu narzędzia Office developer tools w programie Visual Studio.  
  
```vb  
Dim addIn As Office.COMAddIn = Globals.ThisAddIn.Application.COMAddIns.Item("ExcelImportData")  
Dim utilities As ExcelImportData.IAddInUtilities = TryCast( _  
    addIn.Object, ExcelImportData.IAddInUtilities)  
utilities.ImportData()  
```  
  
```csharp  
object addInName = "ExcelImportData";  
Office.COMAddIn addIn = Globals.ThisAddIn.Application.COMAddIns.Item(ref addInName);  
ExcelImportData.IAddInUtilities utilities = (ExcelImportData.IAddInUtilities)addIn.Object;  
utilities.ImportData();  
```  
  
 W tym przykładzie, Jeśli spróbujesz rzutowania wartości <xref:Microsoft.Office.Core.COMAddIn.Object%2A> właściwości `AddInUtilities` klasy, a nie `IAddInUtilities` interfejsu, zgłosi kod <xref:System.InvalidCastException>.  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie dodatków VSTO](../vsto/programming-vsto-add-ins.md)   
 [Wskazówki: Wywoływanie kodu w dodatku VSTO z kodu VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)   
 [Tworzenie rozwiązań pakietu Office](../vsto/developing-office-solutions.md)   
 [Porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Dostosowywanie funkcji interfejsu użytkownika, korzystając z rozszerzalności interfejsów](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)  
  
  