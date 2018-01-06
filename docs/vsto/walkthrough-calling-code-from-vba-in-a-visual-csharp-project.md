---
title: "Wskazówki: Wywoływanie kodu z VBA w projektach Visual C# | Dokumentacja firmy Microsoft"
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
- Excel [Office development in Visual Studio], calling code from VBA
- Word [Office development in Visual Studio], calling code from VBA
- Visual C# [Office development in Visual Studio], calling code from VBA
- workbooks [Office development in Visual Studio], calling code from VBA
- VBA [Office development in Visual Studio], calling code in document-level customizations
- Office documents [Office development in Visual Studio, Visual Basic for Applications and
- calling code from VBA
- document-level customizations [Office development in Visual Studio], calling code
ms.assetid: 9a5741f1-8260-4964-afa1-c69b68d1cfdf
caps.latest.revision: "38"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: a1e61b3b2055e6a32fa1e179232e7366fe2b3d16
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-calling-code-from-vba-in-a-visual-c-project"></a>Wskazówki: wywoływanie kodu z VBA w projektach Visual C#
  W tym przewodniku przedstawiono sposób wywołania metody w dostosowaniu poziomie dokumentu dla programu Microsoft Office Excel z języka Visual Basic dla kodu aplikacji (VBA) w skoroszycie. Procedura obejmuje trzy podstawowe kroki: dodanie metody `Sheet1` elementu klasa obsługująca, ujawnia metody do kodu z VBA w skoroszycie, a następnie wywołaj metodę z kodu VBA w skoroszycie.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Mimo że w tym przewodniku zastosowano programu Excel w szczególności, koncepcje dowodzą wskazówki mają również zastosowanie do projektów na poziomie dokumentu dla programu Word.  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
-   Tworzenie skoroszytu, który zawiera kod VBA.  
  
-   Ufające lokalizacji skoroszytu przy użyciu Centrum zaufania w programie Excel.  
  
-   Dodawanie metody do `Sheet1` hosta klasy elementu.  
  
-   Wyodrębnianie interfejs dla `Sheet1` hosta klasy elementu.  
  
-   Udostępnia metody na kod.  
  
-   Wywoływanie metody z kodu VBA.  
  
> [!NOTE]  
>  Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Program Microsoft Excel  
  
## <a name="creating-a-workbook-that-contains-vba-code"></a>Tworzenie skoroszytu, który zawiera kod VBA  
 Pierwszym krokiem jest tworzenia obsługą makr skoroszytu, który zawiera proste makro języka VBA. Zanim można udostępnianie kodu w VBA dostosowanie, skoroszyt już musi zawierać kod VBA. W przeciwnym razie program Visual Studio nie można zmodyfikować projekt VBA w celu włączenia kod VBA do wywołania w zestawie dostosowania.  
  
 Jeśli masz już skoroszytu, który zawiera kod VBA, który ma być używany, można pominąć ten krok.  
  
#### <a name="to-create-a-workbook-that-contains-vba-code"></a>Aby utworzyć skoroszytu, który zawiera kod VBA  
  
1.  Uruchom program Excel.  
  
2.  Zapisuje aktywny dokument jako **skoroszytu Excel Macro-Enabled (\*xlsm)** o nazwie **WorkbookWithVBA**. Zapisz go w dogodnym miejscu, takich jak pulpit.  
  
3.  Na wstążce kliknij **Developer** kartę.  
  
    > [!NOTE]  
    >  Jeśli **Developer** karta nie jest widoczna, należy go najpierw wyświetlić. Aby uzyskać więcej informacji, zobacz [porady: pokazywanie karty dewelopera na wstążce](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  W **kod** kliknij przycisk **Visual Basic**.  
  
     Zostanie otwarty Edytor Visual Basic.  
  
5.  W **projektu** okna, kliknij dwukrotnie **ThisWorkbook**.  
  
     Plik kodowy dla `ThisWorkbook` obiekt zostanie otwarta.  
  
6.  Dodaj następujący kod VBA do pliku kodu. Ten kod definiuje proste funkcję, która nie działa. Upewnij się, że projekt VBA istnieje w tym skoroszycie jest jedynym celem tej funkcji. Jest to wymagane do wykonania kolejnych kroków tego przewodnika.  
  
    ```  
    Sub EmptySub()  
    End Sub  
    ```  
  
7.  Zapisz dokument i zamknij program Excel.  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
 Teraz można utworzyć projekt poziomie dokumentu dla programu Excel, która korzysta z obsługą makr skoroszyt utworzony wcześniej.  
  
#### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt  
  
1.  Uruchom [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Na **pliku** menu wskaż **nowy**, a następnie kliknij przycisk **projektu**.  
  
3.  W okienku szablonów rozwiń **Visual C#**, a następnie rozwiń węzeł **Office i SharePoint**.  
  
4.  Wybierz **dodatków pakietu Office** węzła.  
  
5.  Na liście szablony projektów, wybierz **skoroszyt programu Excel 2010** lub **skoroszyt programu Excel 2013** projektu.  
  
6.  W **nazwa** wpisz **CallingCodeFromVBA**.  
  
7.  Kliknij przycisk **OK**.  
  
     **Visual Studio Tools dla pakietu Office, Kreator projektu** otwiera.  
  
8.  Wybierz **Skopiuj istniejący dokument**, a następnie, w **pełną ścieżkę istniejącego dokumentu** Określ lokalizację **WorkbookWithVBA** skoroszytu, który został utworzony wcześniej . Jeśli korzystasz z własnego skoroszytu z obsługą makr, należy określić lokalizację tego skoroszytu.  
  
9. Kliknij przycisk **Zakończ**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Otwiera **WorkbookWithVBA** skoroszytu w Projektancie i dodaje **CallingCodeFromVBA** projektu do **Eksploratora rozwiązań**.  
  
## <a name="trusting-the-location-of-the-workbook"></a>Ufające lokalizacji skoroszytu  
 Przed za udostępnianie kodu w rozwiązaniu do kodu z VBA w skoroszycie, muszą ufać VBA w skoroszycie do uruchomienia. Istnieje kilka sposobów, aby to zrobić. W tym przewodniku będzie wykonać to zadanie przez ufające lokalizacji skoroszytu w **Centrum zaufania** w programie Excel.  
  
#### <a name="to-trust-the-location-of-the-workbook"></a>Aby zaufać lokalizacji skoroszytu  
  
1.  Uruchom program Excel.  
  
2.  Kliknij przycisk **pliku** kartę.  
  
3.  Kliknij przycisk **opcje programu Excel** przycisku.  
  
4.  W okienku kategorii kliknij **Centrum zaufania**.  
  
5.  W okienku szczegółów kliknij **ustawienia Centrum zaufania**.  
  
6.  W okienku kategorii kliknij **zaufanych lokalizacji**.  
  
7.  W okienku szczegółów kliknij **Dodaj nową lokalizację**.  
  
8.  W **Microsoft Office zaufanej lokalizacji** okno dialogowe, przejdź do folderu, który zawiera **CallingCodeFromVBA** projektu.  
  
9. Wybierz **podfoldery tej lokalizacji są także zaufane**.  
  
10. W **Microsoft Office zaufanej lokalizacji** okno dialogowe, kliknij przycisk **OK**.  
  
11. W **Centrum zaufania** okno dialogowe, kliknij przycisk **OK**.  
  
12. W **opcje programu Excel** okno dialogowe, kliknij przycisk **OK**.  
  
13. Zakończ **Excel**.  
  
## <a name="adding-a-method-to-the-sheet1-class"></a>Dodawanie metody do Sheet1 — klasa  
 Teraz, kiedy projekt VBA jest skonfigurowane, Dodaj publiczną metodę do `Sheet1` klasy elementu, który można wywołać z kodu VBA hosta.  
  
#### <a name="to-add-a-method-to-the-sheet1-class"></a>Aby dodać metodę do Sheet1 — klasa  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Sheet1.cs**, a następnie kliknij przycisk **kod widoku**.  
  
     **Sheet1.cs** plik zostanie otwarty w edytorze kodu.  
  
2.  Dodaj następujący kod do `Sheet1` klasy. `CreateVstoNamedRange` Metoda tworzy nowy <xref:Microsoft.Office.Tools.Excel.NamedRange> obiekt w określonym zakresie. Ta metoda tworzy także program obsługi zdarzeń dla <xref:Microsoft.Office.Tools.Excel.NamedRange.Selected> zdarzenie <xref:Microsoft.Office.Tools.Excel.NamedRange>. W dalszej części tego przewodnika, wywoła `CreateVstoNamedRange` metody z kodu VBA w dokumencie.  
  
     [!code-csharp[Trin_CallingCSCustomizationFromVBA#2](../vsto/codesnippet/CSharp/CallingCodeFromVBA/Sheet1.cs#2)]  
  
3.  Dodaj następującą metodę do `Sheet1` klasy. Ta metoda zastępuje <xref:Microsoft.Office.Tools.Excel.Worksheet.GetAutomationObject%2A> metody, aby przywrócić bieżące wystąpienie klasy `Sheet1` klasy.  
  
     [!code-csharp[Trin_CallingCSCustomizationFromVBA#3](../vsto/codesnippet/CSharp/CallingCodeFromVBA/Sheet1.cs#3)]  
  
4.  Zastosuj następujące atrybuty przed pierwszym wierszem `Sheet1` deklaracji klasy. Te atrybuty uwidaczniania klasy COM, ale bez generowania interfejsu klasy.  
  
     [!code-csharp[Trin_CallingCSCustomizationFromVBA#1](../vsto/codesnippet/CSharp/CallingCodeFromVBA/Sheet1.cs#1)]  
  
## <a name="extracting-an-interface-for-the-sheet1-class"></a>Wyodrębnianie interfejs dla Sheet1 — klasa  
 Przed mogą uwidaczniać `CreateVstoNamedRange` metoda kod VBA, należy utworzyć publiczny interfejs, który definiuje tę metodę i musi uwidaczniać tego interfejsu do modelu COM.  
  
#### <a name="to-extract-an-interface-for-the-sheet1-class"></a>Aby wyodrębnić interfejsu Sheet1 — klasa  
  
1.  W **Sheet1.cs** kodu z pliku, kliknij w dowolnym miejscu `Sheet1` klasy.  
  
2.  Na **Refaktoryzuj** menu, kliknij przycisk **wyodrębniania interfejsu**.  
  
3.  W **wyodrębniania interfejsu** okna dialogowego, **wybierz publiczne elementy członkowskie, aby utworzyć interfejs** kliknij pozycję `CreateVstoNamedRange` metody.  
  
4.  Kliknij przycisk **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]generuje nowy interfejs o nazwie `ISheet1`, oraz modyfikuje definicji `Sheet1` klasy tak, aby ją implementuje `ISheet1` interfejsu. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]zostanie otwarte także **ISheet1.cs** plik w edytorze kodu.  
  
5.  W **ISheet1.cs** pliku, Zastąp `ISheet1` interfejsu deklaracji z następującym kodem. Ten kod sprawia, że `ISheet1` interfejs publiczny i są one stosowane <xref:System.Runtime.InteropServices.ComVisibleAttribute> atrybutu, aby wyświetlić interfejs do modelu COM.  
  
     [!code-csharp[Trin_CallingCSCustomizationFromVBA#4](../vsto/codesnippet/CSharp/CallingCodeFromVBA/ISheet1.cs#4)]  
  
6.  Skompiluj projekt.  
  
## <a name="exposing-the-method-to-vba-code"></a>Udostępnia metody do kodu VBA  
 Do udostępnienia `CreateVstoNamedRange` metody na kod w tym skoroszycie, ustawienie **ReferenceAssemblyFromVbaProject** właściwość `Sheet1` element hosta do **True**.  
  
#### <a name="to-expose-the-method-to-vba-code"></a>Aby udostępnić metodę kod VBA  
  
1.  W **Eksploratora rozwiązań**, kliknij dwukrotnie **Sheet1.cs**.  
  
     **WorkbookWithVBA** plik zostanie otwarty w Projektancie z Sheet1 — widoczne.  
  
2.  W **właściwości** wybierz **ReferenceAssemblyFromVbaProject** właściwości i zmień wartość na **True**.  
  
3.  Kliknij przycisk **OK** w komunikacie, który jest wyświetlany.  
  
4.  Skompiluj projekt.  
  
## <a name="calling-the-method-from-vba-code"></a>Wywoływanie metody z kodu VBA  
 Można teraz wywołać `CreateVstoNamedRange` metody z kodu VBA w skoroszycie.  
  
> [!NOTE]  
>  W tym przewodniku dodasz kod VBA w skoroszycie podczas debugowania projektu. Kod VBA, które dodasz do tego dokumentu zostaną zastąpione przy następnym uruchomieniu kompilacji projektu, ponieważ kopię dokumentu w folderze głównym projektu programu Visual Studio zastępuje dokumentu w folderze wyjściowym kompilacji. Jeśli chcesz zapisać kod VBA, skopiuj go do dokumentu w folderze projektu. Aby uzyskać więcej informacji, zobacz [łączenie VBA i dostosowywanie na poziomie dokumentu](../vsto/combining-vba-and-document-level-customizations.md).  
  
#### <a name="to-call-the-method-from-vba-code"></a>Wywoływanie metody z kodu VBA  
  
1.  Naciśnij klawisz F5, aby uruchomić projekt.  
  
2.  Na **Developer** karcie **kod** kliknij przycisk **Visual Basic**.  
  
     Zostanie otwarty Edytor Visual Basic.  
  
3.  Na **Wstaw** menu, kliknij przycisk **modułu**.  
  
4.  Dodaj następujący kod do nowego modułu.  
  
     Ten kod wywołuje `CreateTable` metody w zestawie dostosowania. Makra uzyskuje dostęp do tej metody za pomocą globalnej `GetManagedClass` metody dostępu do `Sheet1` hosta elementu klasy, która ujawniony dla kodu języka VBA. `GetManagedClass` Metoda została wygenerowana automatycznie po ustawieniu **ReferenceAssemblyFromVbaProject** właściwość we wcześniejszej części tego przewodnika.  
  
    ```  
    Sub CallVSTOMethod()  
        Dim VSTOSheet1 As CallingCodeFromVBA.Sheet1  
        Set VSTOSheet1 = GetManagedClass(Sheet1)  
        Call VSTOSheet1.CreateVstoNamedRange(Sheet1.Range("A1"), "VstoNamedRange")  
    End Sub  
    ```  
  
5.  Naciśnij F5.  
  
6.  W skoroszycie, kliknij komórkę **A1** na **Sheet1 —**. Sprawdź, czy jest wyświetlany w oknie komunikatu.  
  
7.  Zamknij program Excel bez zapisywania zmian.  
  
## <a name="next-steps"></a>Następne kroki  
 Użytkownik może dowiedzieć się więcej o wywoływanie kodu w rozwiązaniach pakietu Office z VBA w tych tematach:  
  
-   Wywoływanie kodu w elemencie hosta w dostosowaniu Visual Basic z kodu VBA. Ten proces różni się od procesu Visual C#. Aby uzyskać więcej informacji, zobacz [wskazówki: Wywoływanie kodu z VBA w projektach Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md).  
  
-   Wywoływanie kodu w dodatku VSTO z kodu VBA. Aby uzyskać więcej informacji, zobacz [wskazówki: Wywoływanie kodu w dodatku VSTO z kodu VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Łączenie VBA i dostosowywanie na poziomie dokumentu](../vsto/combining-vba-and-document-level-customizations.md)   
 [Programowania dostosowań na poziomie dokumentu](../vsto/programming-document-level-customizations.md)   
 [Porady: udostępnianie kodu z VBA w projektach Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)   
 [Porady: udostępnianie kodu z VBA w Visual C & 35; Projekt](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)   
 [Przewodnik: Wywoływanie kodu z VBA w projektach Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)  
  