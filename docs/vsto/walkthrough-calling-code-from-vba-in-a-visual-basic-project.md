---
title: 'Wskazówki: Wywoływanie kodu z VBA w projektach Visual Basic | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], Visual Basic for Applications and
- ThisDocument class
- Word [Office development in Visual Studio], calling code from VBA
- Visual Basic [Office development in Visual Studio], calling code from VBA
- VBA [Office development in Visual Studio], calling code in document-level customizations
- Office documents [Office development in Visual Studio, Visual Basic for Applications and
- calling code from VBA
- document-level customizations [Office development in Visual Studio], calling code
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: efb8f6c2759760fe2eb5c5d5ccf23e0942eac93a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-calling-code-from-vba-in-a-visual-basic-project"></a>Wskazówki: wywoływanie kodu z VBA w projektach Visual Basic
  W tym przewodniku przedstawiono sposób wywołania metody w dostosowaniu poziomie dokumentu dla programu Microsoft Office Word z języka Visual Basic dla kodu aplikacji (VBA) w dokumencie. Procedura obejmuje trzy podstawowe kroki: dodanie metody `ThisDocument` klasa elementu obsługująca ujawnia metody do kodu VBA i następnie wywołaj metodę z kodu VBA w dokumencie.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Mimo że w tym przewodniku zastosowano programu Word w szczególności pojęcia dowodzą wskazówki dotyczą również projektów na poziomie dokumentu dla programu Excel.  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
-   Tworzenie dokumentu, który zawiera kod VBA.  
  
-   Ufające Lokalizacja dokumentu za pomocą Centrum zaufania w programie Word.  
  
-   Dodawanie metody do `ThisDocument` hosta klasy elementu.  
  
-   Udostępnia metody na kod.  
  
-   Wywoływanie metody z kodu VBA.  
  
> [!NOTE]  
>  Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## <a name="creating-a-document-that-contains-vba-code"></a>Tworzenie dokumentu, który zawiera kod VBA  
 Pierwszym krokiem jest można utworzyć dokumentu z włączoną obsługą makr, który zawiera proste makro języka VBA. Dokument musi zawierać projekt VBA, przed utworzeniem projektu programu Visual Studio, która opiera się na tym dokumencie. W przeciwnym razie program Visual Studio nie można zmodyfikować projekt VBA w celu włączenia kod VBA do wywołania w zestawie dostosowania.  
  
 Jeśli masz już dokument, który zawiera kod VBA, który ma być używany, można pominąć ten krok.  
  
#### <a name="to-create-a-document-that-contains-vba-code"></a>Aby utworzyć dokument, który zawiera kod VBA  
  
1.  Uruchom program Word.  
  
2.  Zapisuje aktywny dokument programu Word **obsługą dokumentu (\*docm)** o nazwie **DocumentWithVBA**. Zapisz go w dogodnym miejscu, takich jak pulpit.  
  
3.  Na wstążce kliknij **Developer** kartę.  
  
    > [!NOTE]  
    >  Jeśli **Developer** karta nie jest widoczna, należy go najpierw wyświetlić. Aby uzyskać więcej informacji, zobacz [porady: pokazywanie karty dewelopera na wstążce](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  W **kod** kliknij przycisk **Visual Basic**.  
  
     Zostanie otwarty Edytor Visual Basic.  
  
5.  W **projektu** okna, kliknij dwukrotnie **ThisDocument**.  
  
     Plik kodowy dla `ThisDocument` obiekt zostanie otwarta.  
  
6.  Dodaj następujący kod VBA do pliku kodu. Ten kod definiuje proste funkcję, która nie działa. Jedynym celem tej funkcji jest upewnij się, że projekt VBA istnieje w dokumencie. Jest to wymagane do wykonania kolejnych kroków tego przewodnika.  
  
    ```  
    Sub EmptySub()  
    End Sub  
    ```  
  
7.  Zapisz dokument i zamknij program Word.  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
 Teraz można utworzyć projekt poziomie dokumentu dla programu Word, który korzysta z obsługą makr dokumentu utworzonego wcześniej.  
  
#### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt  
  
1.  Uruchom [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Na **pliku** menu wskaż **nowy**, a następnie kliknij przycisk **projektu**. Jeśli środowiskiem IDE jest skonfigurowany do używania ustawienia środowiska deweloperskiego Visual Basic, na **pliku** menu, kliknij przycisk **nowy projekt**.  
  
3.  W okienku szablonów rozwiń **Visual Basic**, a następnie rozwiń węzeł **Office i SharePoint**.  
  
4.  Wybierz **dodatków pakietu Office** węzła.  
  
5.  Na liście szablony projektów, wybierz **dokument programu Word 2010** lub **dokument programu Word 2013** projektu.  
  
6.  W **nazwa** wpisz **CallingCodeFromVBA**.  
  
7.  Kliknij przycisk **OK**.  
  
     **Visual Studio Tools dla pakietu Office, Kreator projektu** otwiera.  
  
8.  Wybierz **Skopiuj istniejący dokument**, a następnie, w **pełną ścieżkę istniejącego dokumentu** Określ lokalizację **DocumentWithVBA** dokument, który został utworzony wcześniej . Jeśli korzystasz z własnego dokument z obsługą makr, należy określić lokalizację tego dokumentu.  
  
9. Kliknij przycisk **Zakończ**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Otwiera **DocumentWithVBA** dokumentów w Projektancie i dodaje **CallingCodeFromVBA** projektu do **Eksploratora rozwiązań**.  
  
## <a name="trusting-the-location-of-the-document"></a>Ufające Lokalizacja dokumentu  
 Przed za udostępnianie kodu w rozwiązaniu do kodu z VBA w dokumencie, muszą ufać VBA w dokumencie do uruchomienia. Istnieje kilka sposobów, aby to zrobić. W ramach tego przewodnika zaufania lokalizacji dokumentu w **Centrum zaufania** w programie Word.  
  
#### <a name="to-trust-the-location-of-the-document"></a>Aby zaufać Lokalizacja dokumentu  
  
1.  Uruchom program Word.  
  
2.  Kliknij przycisk **pliku** kartę.  
  
3.  Kliknij przycisk **Word, opcje** przycisku.  
  
4.  W okienku kategorii kliknij **Centrum zaufania**.  
  
5.  W okienku szczegółów kliknij **ustawienia Centrum zaufania**.  
  
6.  W okienku kategorii kliknij **zaufanych lokalizacji**.  
  
7.  W okienku szczegółów kliknij **Dodaj nową lokalizację**.  
  
8.  W **Microsoft Office zaufanej lokalizacji** okno dialogowe, przejdź do folderu, który zawiera **CallingCodeFromVBA** projektu.  
  
9. Wybierz **podfoldery tej lokalizacji są także zaufane**.  
  
10. W **Microsoft Office zaufanej lokalizacji** okno dialogowe, kliknij przycisk **OK**.  
  
11. W **Centrum zaufania** okno dialogowe, kliknij przycisk **OK**.  
  
12. W **Word, opcje** okno dialogowe, kliknij przycisk **OK**.  
  
13. Zamknij program Word.  
  
## <a name="adding-a-method-to-the-thisdocument-class"></a>Dodawanie metody do ThisDocument — klasa  
 Teraz, kiedy projekt VBA jest skonfigurowane, Dodaj metodę `ThisDocument` klasy elementu, który można wywołać z kodu VBA hosta.  
  
#### <a name="to-add-a-method-to-the-thisdocument-class"></a>Aby dodać metodę do ThisDocument — klasa  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **ThisDocument.vb**, a następnie kliknij przycisk **kod widoku**.  
  
     **ThisDocument.vb** plik zostanie otwarty w edytorze kodu.  
  
2.  Dodaj następującą metodę do `ThisDocument` klasy. Ta metoda tworzy tabelę z wierszami i dwie kolumny na początku dokumentu. Parametry Podaj tekst, który jest wyświetlany w pierwszym wierszu. W dalszej części tego przewodnika będzie wywoływać tej metody z kodu VBA w dokumencie.  
  
     [!code-vb[Trin_CallingVBCustomizationFromVBA#1](../vsto/codesnippet/VisualBasic/CallingCodeFromVBA/ThisDocument.vb#1)]  
  
3.  Skompiluj projekt.  
  
## <a name="exposing-the-method-to-vba-code"></a>Udostępnia metody do kodu VBA  
 Do udostępnienia `CreateTable` metody do kodu z VBA w dokumencie, ustawienie **EnableVbaCallers** właściwość `ThisDocument` element hosta do **True**.  
  
#### <a name="to-expose-the-method-to-vba-code"></a>Aby udostępnić metodę kod VBA  
  
1.  W **Eksploratora rozwiązań**, kliknij dwukrotnie **ThisDocument.vb**.  
  
     **DocumentWithVBA** plik zostanie otwarty w projektancie.  
  
2.  W **właściwości** wybierz **EnableVbaCallers** właściwości i zmień wartość na **True**.  
  
3.  Kliknij przycisk **OK** w komunikacie, który jest wyświetlany.  
  
4.  Skompiluj projekt.  
  
## <a name="calling-the-method-from-vba-code"></a>Wywoływanie metody z kodu VBA  
 Można teraz wywołać `CreateTable` metody z kodu VBA w dokumencie.  
  
> [!NOTE]  
>  W tym przewodniku dodasz kod VBA w dokumencie podczas debugowania projektu. Kod VBA, które dodasz do tego dokumentu zostaną zastąpione przy następnym uruchomieniu kompilacji projektu, ponieważ kopię dokumentu w folderze głównym projektu programu Visual Studio zastępuje dokumentu w folderze wyjściowym kompilacji. Jeśli chcesz zapisać kod VBA, skopiuj go do dokumentu w folderze projektu. Aby uzyskać więcej informacji, zobacz [łączenie VBA i dostosowywanie na poziomie dokumentu](../vsto/combining-vba-and-document-level-customizations.md).  
  
#### <a name="to-call-the-method-from-vba-code"></a>Wywoływanie metody z kodu VBA  
  
1.  Naciśnij klawisz F5, aby uruchomić projekt.  
  
2.  Na **Developer** karcie **kod** kliknij przycisk **Visual Basic**.  
  
     Zostanie otwarty Edytor Visual Basic.  
  
3.  Na **Wstaw** menu, kliknij przycisk **modułu**.  
  
4.  Dodaj następujący kod do nowego modułu.  
  
     Ten kod wywołuje `CreateTable` metody w zestawie dostosowania. Makra uzyskuje dostęp do tej metody za pomocą `CallVSTOAssembly` właściwość `ThisDocument` obiektu. Ta właściwość została wygenerowana automatycznie po ustawieniu **EnableVbaCallers** właściwość we wcześniejszej części tego przewodnika.  
  
    ```  
    Sub CreateTable()  
        Call ThisDocument.CallVSTOAssembly.CreateTable("Employee Name", "Start Date")  
    End Sub  
    ```  
  
5.  Naciśnij F5.  
  
6.  Sprawdź, czy nowa tabela została dodana do dokumentu.  
  
7.  Zamknij program Word bez zapisywania zmian.  
  
## <a name="next-steps"></a>Następne kroki  
 Użytkownik może dowiedzieć się więcej o wywoływanie kodu w rozwiązaniach pakietu Office z VBA w tych tematach:  
  
-   Wywoływanie kodu w dostosowania Visual C# z języka VBA. Ten proces jest inna niż proces języka Visual Basic. Aby uzyskać więcej informacji, zobacz [wskazówki: Wywoływanie kodu z VBA w Visual C&#35; projektu](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md).  
  
-   Wywoływanie kodu w dodatku VSTO z kodu VBA. Aby uzyskać więcej informacji, zobacz [wskazówki: Wywoływanie kodu w dodatku VSTO z kodu VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Łączenie VBA i dostosowywanie na poziomie dokumentu](../vsto/combining-vba-and-document-level-customizations.md)   
 [Programowania dostosowań na poziomie dokumentu](../vsto/programming-document-level-customizations.md)   
 [Porady: udostępnianie kodu z VBA w projektach Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)   
 [Porady: udostępnianie kodu z VBA w Visual C&#35; projektu](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)   
 [Wskazówki: Wywoływanie kodu z VBA w Visual C&#35; projektu](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)  
  
  