---
title: 'Wskazówki: Debugowanie formularzy systemu Windows | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], walkthroughs
- debugging managed code, Windows Forms
- debugging [Visual Studio], Windows Forms
- Attach to Process dialog box
- debugger, attaching to programs
- Attach to Process dialog box, walkthroughs
- Windows Forms, debugging
- debugging Windows Forms, walkthroughs
ms.assetid: 529db1e2-d9ea-482a-b6a0-7c543d17f114
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 15e76507b64ea15d390f10cf4896830c03a2c963
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37056805"
---
# <a name="walkthrough-debugging-a-windows-form"></a>Wskazówki: Debugowanie formatu Windows
Formularz systemu Windows jest jedną z najczęściej używanych aplikacji zarządzanych. Formularz systemu Windows tworzy standardową aplikację systemu Windows. Można wykonać instrukcje z tego przewodnika przy użyciu języka Visual Basic, C# lub C++.  
  
 Po pierwsze, należy zamknąć wszystkie otwarte rozwiązania.  
  
### <a name="to-prepare-for-this-walkthrough"></a>Aby przygotować się do tego przewodnika  
  
-   Jeśli masz już otwarte rozwiązanie, zamknij je. (Na **pliku** menu, wybierz opcję **Zamknij rozwiązanie**.)  
  
## <a name="create-a-new-windows-form"></a>Tworzenie nowego formularza systemu Windows  
 Następnie można utworzyć nowy formularz systemu Windows.  
  
#### <a name="to-create-the-windows-form-for-this-walkthrough"></a>Aby utworzyć formularz systemu Windows dla tego przewodnika  
  
1.  Na **pliku** menu, wybierz **nowy** i kliknij przycisk **projektu**.  
  
     **Nowy projekt** zostanie wyświetlone okno dialogowe.  
  
2.  Otwórz w okienku typów projektów **Visual Basic**, **Visual C#**, lub **Visual C++** węzeł, a następnie  
  
    1.  Dla języka Visual Basic lub Visual C#, wybierz **Windows** węzła, następnie wybierz **aplikacji formularzy systemu Windows** w **szablony** okienka.  
  
    2.  W języku Visual C++, wybierz **CLR** węzła, następnie wybierz **aplikacji formularzy systemu Windows** w **szablony** okienka.  
  
3.  W **szablony** okienku wybierz **aplikacji systemu Windows**.  
  
4.  W **nazwa** należy nadać unikatową nazwę (na przykład Walkthrough_SimpleDebug) projektu.  
  
5.  Kliknij przycisk **OK**.  
  
     Visual Studio tworzy nowy projekt i wyświetla nowy formularz w Projektancie Windows Forms. Aby uzyskać więcej informacji, zobacz [Projektant formularzy systemu Windows](http://msdn.microsoft.com/en-us/3c3d61f8-f36c-4d41-b9c3-398376fabb15).  
  
6.  Na **widoku** menu, wybierz opcję **przybornika**.  
  
     Przybornik zostaje otwarty. Aby uzyskać więcej informacji, zobacz [przybornika](../ide/reference/toolbox.md).  
  
7.  W przyborniku kliknij **przycisk** kontroli i przeciągnij formant do warstwy projektowania formularza. Upuść przycisk na formularzu.  
  
8.  W przyborniku kliknij **pole tekstowe** kontroli i przeciągnij formant do warstwy projektowania formularza. Upuść **pole tekstowe** w formularzu.  
  
9. Na powierzchni projektowej formularza, dwukrotnie kliknij przycisk.  
  
     Spowoduje to przejście do strony kodowej. Kursor powinien być w `button1_Click`.  
  
10. W funkcji `button1_Click`, należy dodać następujący kod:  
  
    ```vb  
    textBox1.Text = "Button was clicked!"
    ```  
  
    ```csharp 
    textBox1.Text = "Button was clicked!";
    ```  
  
    ```cpp  
    textBox1->Text = "Button was clicked!";  
    ```  
  
11. Na **kompilacji** menu, wybierz opcję **Kompiluj rozwiązanie**.  
  
     Projekt powinien być kompilowany bez błędów.  
  
## <a name="debug-your-form"></a>Debugowanie formularza  
 Teraz można rozpocząć debugowanie.  
  
#### <a name="to-debug-the-windows-form-created-for-this-walkthrough"></a>Aby debugować formularz systemu Windows utworzony dla tego przewodnika  
  
1.  W oknie źródłowym, należy kliknąć lewy margines w tym samym wierszu, co dodany tekst:  
  
     ```vb  
    textBox1.Text = "Button was clicked!"
    ```  
  
    ```csharp 
    textBox1.Text = "Button was clicked!";
    ```  
  
    ```cpp  
    textBox1->Text = "Button was clicked!";  
    ``` 
  
     Pojawi się czerwona kropka i tekst w wierszu zostanie wyróżniony czerwonym kolorem. Czerwona kropka reprezentuje punkt przerwania. Aby uzyskać więcej informacji, zobacz [punktów przerwania](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583). Po uruchomieniu aplikacji w trybie debugowania, debuger zlokalizuje miejsce trafienia kodu i przerwie tam wykonywanie. Można wówczas wyświetlić stan aplikacji i zdebugować ją.  
  
    > [!NOTE]
    >  Również kliknięciu prawym przyciskiem myszy dowolny wiersz kodu, wskaż pozycję **punktu przerwania**, a następnie kliknij przycisk **wstawić punktu przerwania** Aby dodać punkt przerwania w tym wierszu.  
  
2.  ON **debugowania** menu, wybierz **Start**.  
  
     Formularz systemu Windows zostaje uruchomiony.  
  
3.  W formularzu systemu Windows, należy kliknąć dodany przycisk.  
  
     W programie Visual Studio powoduje to przejście do wiersza, w którym został ustawiony punkt przerwania na stronie kodowej. Ten wiersz powinien być wyróżniony żółtym kolorem. Można teraz wyświetlić zmienne w aplikacji i kontrolować jej wykonanie. Aplikacja zatrzymała teraz wykonywanie, czekając na akcję ze strony użytkownika.  
  
4.  Na **debugowania** menu, wybierz **Windows**, następnie **czujki**i kliknij przycisk **Watch1**.  
  
5.  W **Watch1** kliknij na pusty wiersz. W **nazwa** wpisz `textBox1.Text` (Jeśli używasz programu Visual Basic lub Visual C#) lub `textBox1->Text` (Jeśli używasz C++), naciśnij klawisz ENTER.  
  
     **Watch1** okno zawiera wartość tej zmiennej w cudzysłów jako:  
  
    `""`  
 
6.  Na **debugowania** menu, wybierz **Step Into**.  
  
     Wartość zmian textBox1.Text **Watch1** okno, aby:  
  
    `Button was clicked!`  
  
7.  Na **debugowania** menu, wybierz **Kontynuuj** wznowienie debugowania programu.  
  
8.  W formularzu systemu Windows, należy ponownie kliknąć przycisk.  
  
     Visual Studio ponownie przerywa wykonywanie.  
  
9. Należy kliknąć czerwoną kropkę, która reprezentuje punkt przerwania.  
  
     Spowoduje to usunięcie punktu przerwania z kodu.  
  
10. Na **debugowania** menu, wybierz **Zatrzymaj debugowanie**.  
  
## <a name="attach-to-your-windows-form-application-for-debugging"></a>Dołącz do aplikacji formularza systemu Windows w celu debugowania  
 W [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] można dołączyć debuger do działającego procesu. Jeśli użytkownik wykorzystuje Express Edition, ta funkcja nie jest obsługiwana.  
  
#### <a name="to-attach-to-the-windows-form-application-for-debugging"></a>Aby dołączyć do aplikacji formularza systemu Windows w celu debugowania  
  
1.  W projekcie utworzonym wcześniej, należy kliknąć na lewym marginesie, aby ponownie ustawić punkt przerwania w dodanym wierszu:  
  
     ```vb  
    textBox1.Text = "Button was clicked!"
    ```  
  
    ```csharp 
    textBox1.Text = "Button was clicked!";
    ```  
  
    ```cpp  
    textBox1->Text = "Button was clicked!";   
  
2.  On the **Debug** menu, select **Start Without Debugging**.  
  
     The Windows Form starts running under Windows, just as if you had double-clicked its executable. The debugger is not attached.  
  
3.  On the **Debug** menu, select **Attach to Process**. (This command is also available on the **Tools** menu.)  
  
     The **Attach to Process** dialog box appears.  
  
4.  In the **Available Processes** pane, find the process name (Walkthrough_SimpleDebug.exe) in the **Process** column and click it.  
  
5.  Click the **Attach** button.  
  
6.  In your Windows Form, click the one and only button.  
  
     The debugger breaks execution of the Windows Form at the breakpoint.  
  
## See Also  
 [Debugging Managed Code](../debugger/debugging-managed-code.md)   
 [Debugger Security](../debugger/debugger-security.md)