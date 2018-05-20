---
title: Łączenie VBA i dostosowywanie na poziomie dokumentu
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.VBAInterop.InvalidAssemblyVersion
- VST.VBAInterop.ProjectLoadFailure
- VST.VBAInterop.MissingGUID
- VST.VBAInterop.EnableComCallers
- VST.VBAInterop.PersistVBACode
- VST.VBAInterop.ReferenceAssemblyFromVBA
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], Visual Basic for Applications and
- VBA [Office development in Visual Studio]
- Office documents [Office development in Visual Studio], Visual Basic for Applications and
- VBA [Office development in Visual Studio], about VBA and document-level customizations
- managed code [Office development in Visual Studio], Visual Basic for Applications and
- document-level customizations [Office development in Visual Studio], Visual Basic for Applications and
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a5bc53512a93ad2af9fa30562e54a8419c70c813
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="combine-vba-and-document-level-customizations"></a>Łączenie VBA i dostosowywanie na poziomie dokumentu
  Można użyć języka Visual Basic dla kodu aplikacji (VBA) w dokumencie, który jest częścią dostosowanie poziomie dokumentu dla programu Microsoft Office Word i Microsoft Office Excel. Kod VBA w dokumencie można wywołać z zestawu dostosowania, lub z projektem, aby włączyć kod VBA w dokumencie, aby wywoływać kod w zestawie dostosowania można skonfigurować.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="behavior-of-vba-code-in-a-document-level-customization"></a>Zachowanie kodu VBA w dostosowaniu poziomie dokumentu  
 Po otwarciu projektu w programie Visual Studio, dokument jest otwarty w trybie projektowania. Kod VBA nie działa, gdy dokument jest w trybie projektowania, dzięki czemu można pracować w dokumencie i kodu bez uruchamiania kodu VBA.  
  
 Po uruchomieniu rozwiązania obsługi zdarzeń w VBA i dostosowywanie zestawu odebrania zdarzeń występujących w dokumencie, a następnie uruchom oba zestawy kodu. Nie można ustalić wcześniej kodu, który będzie wykonywany przed innymi; należy określić to testy w każdym przypadku. Jeśli nie dokładnie koordynowane i testowane dwa zestawy kodu można uzyskać nieoczekiwane wyniki.  
  
## <a name="call-vba-code-from-the-customization-assembly"></a>Kod VBA połączenia z zestawu dostosowania  
 Należy wywołać makra w dokumentach programu Word i mogą wywoływać makra i funkcje, które znajdują się w skoroszytach programu Excel. Aby to zrobić, użyj jednej z następujących metod:  
  
-   Dla programu Word, należy wywołać <xref:Microsoft.Office.Interop.Word._Application.Run%2A>metody <xref:Microsoft.Office.Interop.Word.Application> klasy.  
  
-   Dla programu Excel, należy wywołać <xref:Microsoft.Office.Interop.Excel._Application.Run%2A> metody <xref:Microsoft.Office.Interop.Excel.Application> klasy.  
  
 Dla każdej metody pierwszy parametr określa nazwę makra lub funkcji, do której ma zostać wywołana, a pozostałe parametry opcjonalne parametry do przekazania do makra lub funkcji. Pierwszy parametr może mieć różne formaty dla programów Word i Excel:  
  
-   Dla programu Word pierwszy parametr jest ciągiem, który może być dowolną kombinacją szablonu, moduł i nazwę makra. Jeśli określisz nazwy dokumentu, kodu można uruchamiać tylko makra w dokumentów związanych z bieżącego kontekstu — makro nie do dowolnego dokumentów.  
  
-   Dla programu Excel, pierwszy parametr może być ciągiem, który określa nazwę makra <xref:Microsoft.Office.Interop.Excel.Range> wskazuje, gdzie jest funkcja lub Identyfikatora rejestru dla zarejestrowanej funkcji DLL (XLL). W przypadku przekazania ciąg, ciąg zostanie oceniony w kontekście aktywnego arkusza.  
  
 Poniższy przykład kodu pokazuje sposób wywoływania makra o nazwie `MyMacro` z projektu poziomie dokumentu dla programu Excel. W tym przykładzie założono, że `MyMacro` jest zdefiniowany w `Sheet1`.  
  
```vb  
Globals.Sheet1.Application.Run("MyMacro")  
```  
  
```csharp  
Globals.Sheet1.Application.Run("MyMacro", missing, missing, missing,  
    missing, missing, missing, missing, missing, missing, missing,  
    missing, missing, missing, missing, missing, missing, missing,  
    missing, missing, missing, missing, missing, missing, missing,   
    missing, missing, missing, missing, missing, missing);  
```  
  
> [!NOTE]  
>  Aby uzyskać informacje o korzystaniu z globalnej `missing` zmiennej zamiast następujące parametry opcjonalne języka Visual C#, zobacz [napisać kod w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md).  
  
## <a name="call-code-in-document-level-customizations-from-vba"></a>Wywoływanie kodu w dostosowaniach na poziomie dokumentu z VBA  
 Można skonfigurować projekt poziomie dokumentu dla programu Word i Excel, ten kod Visual Basic for Applications (VBA) w dokumencie można wywoływać kod w zestawie dostosowania. Jest to przydatne w następujących scenariuszach:  
  
-   Chcesz rozszerzyć istniejącego kodu z VBA w dokumencie przy użyciu funkcji w dostosowania poziomie dokumentu, który jest skojarzony z tym samym dokumencie.  
  
-   Chcesz udostępnić usługi tworzonych w dostosowaniu poziomie dokumentu dla użytkowników końcowych, którzy mogą uzyskać dostęp do usług pisanie kodu VBA w dokumencie.  
  
 Narzędzia Office development w Visual Studio podanie dodatków VSTO podobnych funkcji. Jeśli tworzysz dodatku VSTO można wywołać w dodatku VSTO z kodu z innych rozwiązań Microsoft Office. Aby uzyskać więcej informacji, zobacz [wywoływanie kodu w dodatkach VSTO z innych rozwiązań pakietu Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).  
  
> [!NOTE]  
>  Nie można użyć tej funkcji w projektach szablon programu Word. Może służyć tylko w dokument programu Word, skoroszyt programu Excel lub projekty szablonu programu Excel.  
  
## <a name="requirements"></a>Wymagania  
 Przed włączeniem kod VBA do wywołania w zestawie dostosowania projektu musi spełniać następujące wymagania:  
  
-   Dokument musi mieć jedną z następujących rozszerzeń nazw plików:  
  
    -   Dla programu Word: *docm* lub *doc*  
  
    -   Dla programu Excel: *xlsm*, *xltm*, *xls*, lub *xlt*  
  
-   Dokument już musi zawierać projekt VBA, który ma kod VBA w nim.  
  
-   Kod VBA w dokumencie musi mieć możliwość uruchamiania bez monitowania użytkownika o włączenie makr. Zaufany kod VBA przez dodanie lokalizacji projektu pakietu Office do listy zaufanych lokalizacji w ustawieniach Centrum zaufania dla programu Word i Excel.  
  
-   Office project musi zawierać co najmniej jedną klasę publicznego, który zawiera co najmniej jednego członka publicznego, które wyświetlasz VBA.  
  
     Można ujawniać metod, właściwości i zdarzeń do języka VBA. Klasa, która naraża może być klasą elementu hosta (takich jak `ThisDocument` dla programu Word, lub `ThisWorkbook` i `Sheet1` dla programu Excel) lub innej klasy, która należy zdefiniować w projekcie. Aby uzyskać informacje o obiektach hosta, zobacz [elementów, a informacje o formantach](../vsto/host-items-and-host-controls-overview.md).  
  
## <a name="enable-vba-code-to-call-into-the-customization-assembly"></a>Włącz kod VBA do wywołania w zestawie dostosowania  
 Istnieją dwa różne sposoby, że mogą uwidaczniać elementów członkowskich w zestawie dostosowania do kodu z VBA w dokumencie:  
  
-   Mogą uwidaczniać elementy członkowskie klasy elementu hosta w [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] projektu VBA. W tym celu należy ustawić **EnableVbaCallers** właściwości elementu hosta do **True** w **właściwości** okno podczas element hosta (to znaczy dokumentu, arkusza lub skoroszyt) Otwórz w projektancie. Visual Studio automatycznie wykonuje wszystkie informacje o pracy wymagane do włączenia kod VBA wywoła członków klasy.  
  
-   Mogą uwidaczniać elementów członkowskich w dowolnej klasy publicznej w projektach Visual C# lub elementy członkowskie z systemem innym niż hoście elementu klasy w [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] projektu VBA. Opcja ta zapewnia większą swobodę Wybierz klasy, które ujawnia VBA, ale również wymaga więcej czynności ręcznych.  
  
     Aby to zrobić, należy wykonać następujące główne kroki:  
  
    1.  Udostępnianie klasy do modelu COM.  
  
    2.  Zastąpienie **GetAutomationObject** metody klasy elementu hosta w projekcie można zwrócić wystąpienia klasy, która wyświetlasz VBA.  
  
    3.  Ustaw **ReferenceAssemblyFromVbaProject** właściwości każdej klasy elementu hosta w projekcie do **True**. Osadza zestawu dostosowywania biblioteki typów w zestawie i dodaje odwołanie do biblioteki typów dla projektu VBA w dokumencie.  
  
 Aby uzyskać szczegółowe instrukcje, zobacz [porady: udostępnianie kodu z VBA w projektach Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md) i [porady: udostępnianie kodu z VBA w Visual C&#35; projektu](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md).  
  
 **EnableVbaCallers** i **ReferenceAssemblyFromVbaProject** właściwości są dostępne tylko w **właściwości** okna w czasie projektowania; nie można użyć w czasie wykonywania . Aby wyświetlić właściwości, należy otworzyć projektanta dla elementu hosta w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Aby uzyskać więcej informacji na temat określonych zadań, które wykonuje program Visual Studio podczas ustawiania tych właściwości, zobacz [zadania wykonywane przez hosta właściwości elementu](#PropertyTasks).  
  
> [!NOTE]  
>  Jeśli skoroszytu lub dokument nie zawiera kodu VBA lub jeśli kod VBA w dokumencie nie jest zaufany do uruchomienia, zostanie wyświetlony komunikat o błędzie w przypadku ustawienia **EnableVbaCallers** lub **ReferenceAssemblyFromVbaProject**  właściwości **True**. Jest to spowodowane Visual Studio nie może modyfikować projektu VBA w dokumencie w takiej sytuacji.  
  
## <a name="use-members-in-vba-code-to-call-into-the-customization-assembly"></a>Użyj elementów członkowskich w kodzie języka VBA do wywołania w zestawie dostosowania  
 Po skonfigurowaniu projektu do włączenia kodu VBA do wywołania w zestawie dostosowania programu Visual Studio dodaje następujące elementy członkowskie do projektu VBA w dokumencie:  
  
-   Dla wszystkich projektów programu Visual Studio dodaje globalny metodę o nazwie `GetManagedClass`.  
  
-   Dla [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] projektów, w których uwidacznia członkami hosta elementu klasy przy użyciu **EnableVbaCallers** właściwość, Visual Studio również dodaje właściwość o nazwie `CallVSTOAssembly` do `ThisDocument`, `ThisWorkbook`, `Sheet1`, `Sheet2`, lub `Sheet3` modułu w projekcie języka VBA.  
  
 Można użyć `CallVSTOAssembly` właściwości lub `GetManagedClass` metodę, aby dostęp do publicznych elementów członkowskich klasy, która ujawniony dla kodu z VBA w projekcie.  
  
> [!NOTE]  
>  Podczas tworzenia i wdrażania rozwiązania, istnieje kilka różnych kopii dokumentu którym można dodać kod VBA. Aby uzyskać więcej informacji, zobacz [wytyczne dotyczące dodawania VBA kodu w dokumencie](#Guidelines).  
  
### <a name="use-the-callvstoassembly-property-in-a-visual-basic-project"></a>Użyj właściwości CallVSTOAssembly w projektach Visual Basic  
 Użyj `CallVSTOAssembly` dostępu publiczne elementy członkowskie dodane do elementu klasy obsługującej dla właściwości. Na przykład następujące makra VBA wywołuje metodę o nazwie `MyVSTOMethod` zdefiniowanego w `Sheet1` klasy w projekcie skoroszytu programu Excel.  
  
```  
Sub MyMacro()  
    Sheet1.CallVSTOAssembly.MyVSTOMethod()  
End Sub  
```  
  
 Ta właściwość jest bardziej wygodne wywołują zestawu dostosowania niż przy użyciu `GetManagedClass` metody bezpośrednio. `CallVSTOAssembly` Zwraca obiekt reprezentujący hosta klasy element zostanie ujawniony VBA. Elementy członkowskie i parametrów metod zwróconego obiektu są wyświetlane w IntelliSense.  
  
 `CallVSTOAssembly` Właściwość ma deklaracji, która jest podobny do następującego kodu. Ten kod przyjęto założenie, że zostały udostępnione `Sheet1` hosta klasy elementu w projekcie skoroszytu programu Excel o nazwie `ExcelWorkbook1` VBA.  
  
```  
Property Get CallVSTOAssembly() As ExcelWorkbook1.Sheet1  
    Set CallVSTOAssembly = GetManagedClass(Me)  
End Property  
```  
  
### <a name="use-the-getmanagedclass-method"></a>Użyj metody GetManagedClass  
 Aby użyć globalnej `GetManagedClass` metody, przekaż obiekt VBA, który odpowiada do klasy elementu hosta, który zawiera zastąpienia z **GetAutomationObject** — metoda. Następnie uzyskiwanie dostępu do klasy, która narażonych na VBA za pomocą zwrócony obiekt.  
  
 Na przykład następujące makra VBA wywołuje metodę o nazwie `MyVSTOMethod` zdefiniowanego w `Sheet1` hosta klasy elementu w projekcie skoroszytu programu Excel o nazwie `ExcelWorkbook1`.  
  
```  
Sub CallVSTOMethod  
    Dim VSTOSheet1 As ExcelWorkbook1.Sheet1  
    Set VSTOSheet1 = GetManagedClass(Sheet1)  
    VSTOSheet1.MyVSTOMethod  
End Sub  
```  
  
 `GetManagedClass` Metoda ma następujące oświadczenie.  
  
```  
GetManagedClass(pdispInteropObject Object) As Object  
```  
  
 Ta metoda zwraca obiekt reprezentujący klasę, która zostanie ujawniony VBA. Elementy członkowskie i parametrów metod zwróconego obiektu są wyświetlane w IntelliSense.  
  
##  <a name="Guidelines"></a> Wytyczne dotyczące dodawania kod VBA do dokumentu  
 Istnieje kilka różnych kopii dokumentu, którym można dodać kod VBA, który odwołuje się do dostosowania poziomie dokumentu.  
  
 Tworzenie i testowanie rozwiązania, można napisać kod VBA w dokumencie, który zostanie otwarty podczas debugowania i uruchom projekt w programie Visual Studio (to znaczy dokument w folderze wyjściowym kompilacji). Jednak kod VBA dodanych do tego dokumentu zostaną zastąpione przy następnym uruchomieniu kompilacji projektu, ponieważ kopię dokumentu w folderze głównym projektu programu Visual Studio zastępuje dokumentu w folderze wyjściowym kompilacji.  
  
 Jeśli chcesz zapisać kod VBA Dodaj do dokumentu, podczas debugowania i uruchamiania rozwiązania, skopiuj kod VBA do dokumentu w folderze projektu. Aby uzyskać więcej informacji na temat procesu kompilacji, zobacz [tworzenie rozwiązań pakietu office](../vsto/building-office-solutions.md).  
  
 Gdy wszystko będzie gotowe do wdrożenia rozwiązania, istnieją trzy lokalizacje głównego dokumentu, w których można dodać kod VBA.  
  
### <a name="in-the-project-folder-on-the-development-computer"></a>W folderze projektu na komputerze dewelopera  
 Ta lokalizacja jest wygodne, jeśli masz pełną kontrolę nad zarówno kod VBA w dokumencie i kod dostosowania. Ponieważ dokument jest na komputerze dewelopera, można łatwo zmodyfikować kod VBA zmiana kodu dostosowania. Kod VBA dodać tę kopię dokumentu pozostaje w dokumencie podczas kompilacji, debugowanie i publikowanie rozwiązania.  
  
 Kod VBA nie można dodać do dokumentu, gdy jest on otwarty w projektancie. Należy najpierw zamknąć dokument w projektancie, a następnie otwórz dokument bezpośrednio w Word czy Excel.  
  
> [!CAUTION]  
>  Jeśli dodasz kod VBA uruchamiany po otwarciu dokumentu w rzadkich przypadkach ten kod może spowodować uszkodzenie dokumentu lub uniemożliwić otwarcie w projektancie.  
  
### <a name="in-the-publish-or-installation-folder"></a>W folderze publikowania lub instalacji  
 W niektórych przypadkach może być odpowiedni dodać kod VBA do dokumentu w folderze publikowania lub instalacji. Na przykład wybierz tę opcję, jeśli kod VBA jest zapisywane i przetestowane przez dewelopera innego komputera, który nie ma zainstalowanego programu Visual Studio.  
  
 Jeśli użytkownicy zainstalują rozwiązanie bezpośrednio z folderu publikowania, należy dodać kodu VBA w dokumencie za każdym razem, gdy publikowanie rozwiązania. Visual Studio zastępuje dokument w lokalizacji publikowania rozwiązania.  
  
 Jeśli użytkownicy zainstalują rozwiązania z folderu instalacji, który różni się od folderu publikowania, można uniknąć, dodawać kod VBA w dokumencie za każdym razem, gdy publikowanie rozwiązania. Podczas aktualizacji publikowania jest gotowa do przeniesienia z folderu publikowania do folderu instalacji, skopiuj wszystkie pliki do folderu instalacji z wyjątkiem dokumentu.  
  
### <a name="on-the-end-user-computer"></a>Na komputerze użytkownika końcowego  
 Jeśli użytkownicy końcowi VBA deweloperów, którzy są wywoływanie usługi, które zapewniają w dostosowania poziomie dokumentu, można ustalić ich sposób wywoływania kodu za pomocą `CallVSTOAssembly` właściwości lub `GetManagedClass` metody w swoich kopii dokumentu. Po opublikowaniu aktualizacji do rozwiązania, kod VBA w dokumencie na komputerze użytkownika końcowego nie zostaną zastąpione, ponieważ dokument nie jest modyfikowany przez publikowanie aktualizacji.  
  
##  <a name="PropertyTasks"></a> Zadania wykonywane przez hosta właściwości elementu  
 Jeśli używasz **EnableVbaCallers** i **ReferenceAssemblyFromVbaProject** właściwości, Visual Studio wykonuje różne zestawy zadań.  
  
### <a name="enablevbacallers"></a>EnableVbaCallers  
 Podczas ustawiania **EnableVbaCallers** właściwości elementu hosta do **True** w projektach Visual Basic, Visual Studio wykonuje następujące zadania:  
  
1.  Dodaje <xref:Microsoft.VisualBasic.ComClassAttribute> i <xref:System.Runtime.InteropServices.ComVisibleAttribute> atrybutów do klasy elementu host.  
  
2.  Zastępuje on **GetAutomationObject** metody klasy elementu host.  
  
3.  Ustawia **ReferenceAssemblyFromVbaProject** właściwości elementu hosta do **True**.  
  
 Podczas ustawiania **EnableVbaCallers** właściwości z powrotem do **False**, Visual Studio wykonuje następujące zadania:  
  
1.  Usuwa <xref:Microsoft.VisualBasic.ComClassAttribute> i <xref:System.Runtime.InteropServices.ComVisibleAttribute> atrybutów z `ThisDocument` klasy.  
  
2.  Usuwa **GetAutomationObject** metody z klasy elementu host.  
  
    > [!NOTE]  
    >  Program Visual Studio nie ustawia automatycznie **ReferenceAssemblyFromVbaProject** właściwości z powrotem do **False**. Tę właściwość można ustawić, **False** ręcznie przy użyciu **właściwości** okna.  
  
### <a name="referenceassemblyfromvbaproject"></a>ReferenceAssemblyFromVbaProject  
 Gdy **ReferenceAssemblyFromVbaProject** ma ustawioną właściwość elementu hosta w projektach Visual Basic lub Visual C# **True**, Visual Studio wykonuje następujące zadania:  
  
1.  Generuje biblioteki typów dla zestawu dostosowania, a osadza biblioteki typów w zestawie.  
  
2.  Dodaje odwołania do następujących bibliotek typów w projekcie VBA w dokumencie:  
  
    -   Biblioteki typów dla używanego zestawu dostosowania.  
  
    -   Microsoft Visual Studio Tools dla pakietu Office wykonanie aparat 9.0 biblioteki typów. Ta biblioteka typów jest uwzględniona w [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
 Gdy **ReferenceAssemblyFromVbaProject** właściwości jest ustawiana dla **False**, Visual Studio wykonuje następujące zadania:  
  
1.  Usuwa odwołania do biblioteki typu z projektu VBA w dokumencie.  
  
2.  Usuwa biblioteki osadzonych typów z zestawu.  
  
## <a name="troubleshoot"></a>Rozwiązywanie problemów
 W poniższej tabeli wymieniono niektóre typowe błędy i sugestie dotyczące poprawiania błędów.  
  
|Błąd|Sugestia|  
|-----------|----------------|  
|Po ustawieniu **EnableVbaCallers** lub **ReferenceAssemblyFromVbaProject** właściwości, komunikat o błędzie stwierdza, że dokument nie zawiera projektu VBA lub nie masz uprawnień dostępu do Projekt VBA w dokumencie.|Sprawdź, czy dokument w projekcie zawiera co najmniej jeden makro VBA, projekt VBA relacją zaufania wystarczające do uruchomienia i projektu VBA nie jest chroniony hasłem.|  
|Po ustawieniu **EnableVbaCallers** lub **ReferenceAssemblyFromVbaProject** właściwości, komunikat o błędzie stanów <xref:System.Runtime.InteropServices.GuidAttribute> deklaracji lub jest uszkodzony.|Upewnij się, że <xref:System.Runtime.InteropServices.GuidAttribute> deklaracji znajduje się w *AssemblyInfo.cs* lub *AssemblyInfo.vb* pliku w projekcie i że tego atrybutu jest ustawiona na prawidłowy identyfikator GUID.|  
|Po ustawieniu **EnableVbaCallers** lub **ReferenceAssemblyFromVbaProject** właściwości, komunikat o błędzie stwierdza, że numer wersji określony przez <xref:System.Reflection.AssemblyVersionAttribute> jest nieprawidłowy.|Upewnij się, że <xref:System.Reflection.AssemblyVersionAttribute> deklaracji w *AssemblyInfo.cs* lub *AssemblyInfo.vb* pliku w projekcie ma ustawioną wartość numeru wersji prawidłowym zestawem. Aby uzyskać informacje o numerach wersji prawidłowy zestaw, zobacz <xref:System.Reflection.AssemblyVersionAttribute> klasy.|  
|Po zmianie nazwy zestawu dostosowania, kod VBA, który odwołuje się do zestawu dostosowania przestanie działać.|Jeśli zmienisz nazwę zestawu dostosowania po jest narażony na kod, powiązanie projekt VBA w dokumencie i używanemu zestawowi dostosowania zostanie przerwane. Aby rozwiązać ten problem, zmień **ReferenceFromVbaAssembly** właściwości w swoim projekcie **False** , a następnie z powrotem do **True**, a następnie Zastąp wszystkie odwołania do zestawu starego Nazwa w kodzie języka VBA z nową nazwą zestawu.|  
  
## <a name="see-also"></a>Zobacz także  
 [Porady: udostępnianie kodu z VBA w projektach Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)   
 [Porady: udostępnianie kodu z VBA w Visual C&#35; projektu](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)   
 [Wskazówki: Wywoływanie kodu z VBA w projektach Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)   
 [Wskazówki: Wywoływanie kodu z VBA w Visual C&#35; projektu](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)   
 [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)   
 [Rozwiązania VBA i pakietu Office w Visual Studio](../vsto/vba-and-office-solutions-in-visual-studio-compared.md)   
 [Dostosowywanie na poziomie dokumentu programu](../vsto/programming-document-level-customizations.md)  
  
  