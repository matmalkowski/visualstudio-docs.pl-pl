---
title: 'Wskazówki: Debugowanie formularzy sieci Web | Dokumentacja firmy Microsoft'
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
- Web pages [.NET Framework], debugging
- Web sites [.NET Framework], debugging
- ASP.NET, debugging Web applications
- Web applications [.NET Framework], debugging
- ASP.NET Web sites, debugging
- ASP.NET Web pages, debugging
- debugging ASP.NET Web applications, Web Forms
- debugging [Visual Studio], Web Forms
ms.assetid: e2b4fa14-8f5b-444d-a903-54070b784bd4
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 22fd6f033dd76e15311912256bc0597dfc3260c6
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="walkthrough-debugging-a-web-form"></a>Wskazówki: debugowanie formularzy sieci Web
Kroki opisane w tym przewodniku opisano, jak debugować [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] sieci Web aplikacji, znanej także jako formularza sieci Web. Przedstawiono sposób uruchamiania i zatrzymuje wykonywanie, ustaw punkty przerwania i Sprawdź zmienne w **czujki** okna.  
  
> [!NOTE]
>  W tym przewodniku, trzeba mieć uprawnienia administratora na komputerze serwera. Domyślnie [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] procesu, aspnet_wp.exe lub w3wp.exe, działa jako [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] procesu. Aby debugować [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], musisz mieć uprawnienia administratora na komputerze, gdzie [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] uruchamia go. Aby uzyskać więcej informacji, zobacz [wymagania systemowe](../debugger/aspnet-debugging-system-requirements.md).  
  
 Okna dialogowe i dostępne polecenia menu mogą różnić się od opisanych w pomocy, w zależności od wersji lub aktywne ustawienia. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-create-the-web-form"></a>Aby utworzyć formularz sieci Web  
  
1.  Jeśli masz już otwartego rozwiązania, należy go zamknąć.  
  
2.  Na **pliku** menu, kliknij przycisk **nowy**, a następnie kliknij przycisk **witryny sieci Web**.  
  
     **Nowej witryny sieci Web** zostanie wyświetlone okno dialogowe.  
  
3.  W **szablony** okienku, kliknij przycisk **witryny sieci Web ASP.NET**.  
  
4.  Na **lokalizacji** wiersz, kliknij przycisk **HTTP** z listy, a w polu tekstowym, wpisz **http://localhost/WebSite**.  
  
5.  W **języka** kliknij **Visual C#** lub **Visual Basic**.  
  
6.  Kliknij przycisk **OK**.  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Tworzy nowy projekt i wyświetla domyślny kod źródłowy HTML. Tworzy także nowy katalog wirtualny o nazwie **witryny sieci Web** w obszarze **domyślna witryna sieci Web** w usługach IIS.  
  
7.  Kliknij przycisk **projekt** kartę na dolny margines.  
  
8.  Kliknij przycisk **przybornika** karcie na lewym marginesie, lub wybierz ją na **widoku** menu.  
  
     **Przybornika** otwiera.  
  
9. W **przybornika**, kliknij przycisk **przycisk** sterować i dodaj go do powierzchni projektu głównego, Default.aspx.  
  
10. W **przybornika**, kliknij przycisk **pole tekstowe** kontroli i przeciągnij formant na powierzchnię projektu głównego, Default.aspx.  
  
11. Kliknij dwukrotnie upuszczony formantu przycisku.  
  
     Powoduje to przejście na stronę kodową: Default.aspx.cs dla języka C# lub Default.aspx.vb dla [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. Kursor musi należeć do funkcji `Button1_Click`.  
  
12. W `Button1_Click` funkcji, Dodaj następujący kod:  
  
    ```  
    ' Visual Basic  
    TextBox1.Text = "Button was clicked!"  
  
    // C#  
    TextBox1.Text = "Button was clicked!";  
    ```  
  
13. Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.  
  
     Projekt powinien utworzyć bez błędów.  
  
     Teraz można przystąpić do uruchomienia debugowania.  
  
### <a name="to-debug-the-web-form"></a>Aby debugować formularza sieci Web  
  
1.  W oknie Default.aspx.cs lub Default.aspx.vb kliknij lewy margines, w tym samym wierszu jako tekst, który zostanie dodany:  
  
    ```  
    ' Visual Basic  
    TextBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
    ```  
  
     Pojawi się czerwona kropka i tekst w wierszu zostanie wyróżniony czerwonym kolorem. Czerwona kropka reprezentuje punkt przerwania. Po uruchomieniu aplikacji w trybie debugowania, debuger zlokalizuje miejsce trafienia kodu i przerwie tam wykonywanie. Można wówczas wyświetlić stan aplikacji i zdebugować ją. Aby uzyskać więcej informacji, zobacz [punktów przerwania](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
2.  Na **debugowania** menu, kliknij przycisk **Rozpocznij debugowanie**.  
  
3.  **Włączone debugowanie nie** zostanie wyświetlone okno dialogowe. Wybierz **zmodyfikować plik Web.config w celu włączenia debugowania** opcji, a następnie kliknij przycisk **OK**.  
  
     Internet Explorer rozpoczyna się i zostanie wyświetlona strona, która została zaprojektowana.  
  
4.  W programie Internet Explorer kliknij przycisk.  
  
     W [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], powoduje to przejście do wiersza gdzie Ustaw punkt przerwania na stronę kodową Default.aspx.cs lub Default.aspx.vb. Ten wiersz powinien być wyróżniony żółtym kolorem. Można teraz wyświetlić zmienne w aplikacji i kontrolować jej wykonanie. Zatrzymuje wykonywanie i czeka na polecenie z Twojej aplikacji.  
  
5.  Na **debugowania** menu, kliknij przycisk **Windows**, następnie kliknij przycisk **czujki**, a następnie kliknij przycisk **Watch1**.  
  
6.  W **czujki** wpisz **TextBox1.Text**.  
  
     **Czujki** okno zawiera wartość zmiennej `TextBox1.Text`:  
  
    ```  
    ""  
    ```  
  
7.  Na **debugowania** menu, kliknij przycisk **Step Over**.  
  
     Wartość `TextBox1.Text` zmiany w **czujki** okna do odczytu:  
  
    ```  
    "Button was clicked!"  
    ```  
  
8.  Na **debugowania** menu, kliknij przycisk **Kontynuuj**.  
  
9. W programie Internet Explorer kliknij ponownie przycisk.  
  
     Wykonanie ponownie zatrzymuje się na punkt przerwania.  
  
10. W oknie Default.aspx.cs lub Default.aspx.vb kliknij czerwonej kropki na lewym marginesie.  
  
     Spowoduje to usunięcie punktu przerwania.  
  
11. Na **debugowania** menu, kliknij przycisk **Zatrzymaj debugowanie**.  
  
### <a name="to-attach-to-the-web-form-for-debugging"></a>Aby dołączyć do formularza sieci Web do debugowania  
  
1.  W [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] można dołączyć debuger do działającego procesu. Najbardziej efektywne, debugowanie, skompiluj plik wykonywalny jako wersja do debugowania z plików symboli (PDB).  
  
2.  W oknie Default.aspx.cs lub Default.aspx.vb kliknij lewy margines ponownie ustawić punkt przerwania w wierszu dodane:  
  
    ```  
    ' Visual Basic  
    TextBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
    ```  
  
3.  Na **debugowania** menu, kliknij przycisk **uruchomić bez debugowania**.  
  
     Formularz sieci Web zaczyna być uruchamiana w programie Internet Explorer, ale nie jest dołączony debuger.  
  
4.  Dołącz do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] procesu. Aby uzyskać więcej informacji, zobacz [debugowania wdrożonych aplikacji sieci Web](../debugger/debugging-deployed-web-applications.md).  
  
5.  W programie Internet Explorer kliknij przycisk w formularzu.  
  
     W [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], powinien trafienie punktu przerwania w Default.aspx.cs, Default.aspx.vb lub Default.aspx.  
  
6.  Po zakończeniu debugowania na **debugowania** menu, kliknij przycisk **Zatrzymaj debugowanie**.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)