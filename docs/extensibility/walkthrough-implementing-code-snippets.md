---
title: 'Wskazówki: Wdrażanie wstawki kodu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ae260951160bc3d4ed3bb1535f47eb1f33649957
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-implementing-code-snippets"></a>Wskazówki: Wdrażanie wstawki kodu
Można utworzyć fragmentów kodu i dołącz je rozszerzenia edytora, aby użytkownicy rozszerzenia można dodać je do ich własnych kodu.  
  
 Fragment kodu to fragment kodu lub innych tekst, który może być zawarte w pliku. Aby wyświetlić wszystkie fragmenty kodu, które zostały zarejestrowane dla określonych języków programowania, na **narzędzia** menu, kliknij przycisk **Menedżer wstawek kodu**. Aby wstawić fragment kodu w pliku, kliknij prawym przyciskiem myszy miejsce fragment kodu, kliknij przycisk **wstawić fragment** lub **z funkcji Otocz przez**Znajdź fragment ma i kliknij go dwukrotnie. Naciśnij klawisz TAB lub klawisze SHIFT + TAB, aby zmodyfikować odpowiednich części fragmentu, a następnie naciśnij klawisz ENTER lub ESC, aby zaakceptować. Aby uzyskać więcej informacji, zobacz [wstawki kodu](../ide/code-snippets.md).  
  
 Fragment kodu znajduje się w pliku XML, który ma rozszerzenie nazwy pliku .snippet. Fragment może zawierać pola, które są wyróżnione po wstawieniu fragmentu, dzięki czemu użytkownik może znaleźć i należy je zmienić. Fragment pliku zawiera również informacje dotyczące **Menedżer wstawek kodu** tak, aby możliwe było wyświetlanie nazwy fragment w odpowiedniej kategorii. Informacje o schemacie fragment, zobacz [fragmenty kodu — odwołanie do schematu](../ide/code-snippets-schema-reference.md).  
  
 Ten przewodnik zawiera instrukcje wykonać te zadania:  
  
1.  Utwórz i zarejestruj wstawki kodu dla określonego języka.  
  
2.  Dodaj **wstawić fragment** poleceń do menu skrótów.  
  
3.  Implementuje fragment rozszerzenia.  
  
 Ten przewodnik jest oparty na [wskazówki: wyświetlanie uzupełniania](../extensibility/walkthrough-displaying-statement-completion.md).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, użytkownik nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest uwzględniona jako opcjonalna funkcja w Instalatorze programu Visual Studio. Można także zainstalować zestawu SDK dla programu późniejsze. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-and-registering-code-snippets"></a>Tworzenie i rejestrowanie wstawki kodu  
 Zazwyczaj wstawki kodu są skojarzone z usługą zarejestrowanych języka. Jednak nie trzeba zaimplementować <xref:Microsoft.VisualStudio.Package.LanguageService> zarejestrować wstawki kodu. Zamiast tego po prostu określić identyfikator GUID w pliku indeksu fragment kodu, a następnie użyć tego samego identyfikatora GUID w <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> dodany do projektu.  
  
 Następująca procedura przedstawia sposób tworzenia fragmentów kodu i skojarzyć je z określonym identyfikatorem GUID.  
  
1.  Utwórz następującą strukturę katalogów:  
  
     **%InstallDir%\TestSnippets\Snippets\1033\\**  
  
     gdzie *InstallDir %* jest folder instalacji programu Visual Studio. (Mimo że ta ścieżka jest zwykle używana do zainstalowania wstawki kodu, można określić dowolną ścieżkę).  
  
2.  W folderze \1033\, należy utworzyć plik XML i nadaj jej nazwę **TestSnippets.xml**. (Mimo że ta nazwa jest zwykle używana dla pliku indeksu fragment, można określić dowolną nazwę, jak długo ma rozszerzenie nazwy pliku .xml.) Dodaj poniższy tekst, a następnie usunąć symbol zastępczy identyfikator GUID i dodać własne.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <SnippetCollection>  
        <Language Lang="TestSnippets" Guid="{00000000-0000-0000-0000-000000000000}">  
            <SnippetDir>  
                <OnOff>On</OnOff>  
                <Installed>true</Installed>  
                <Locale>1033</Locale>  
                <DirPath>%InstallRoot%\TestSnippets\Snippets\%LCID%\</DirPath>  
                <LocalizedName>Snippets</LocalizedName>  
            </SnippetDir>  
        </Language>  
    </SnippetCollection>  
    ```  
  
3.  Utwórz plik w folderze fragment, nadaj jej nazwę **test**`.snippet`, a następnie dodaj następujący tekst:  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <CodeSnippets  xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
        <CodeSnippet Format="1.0.0">  
            <Header>  
                <Title>Test replacement fields</Title>  
                <Shortcut>test</Shortcut>  
                <Description>Code snippet for testing replacement fields</Description>  
                <Author>MSIT</Author>  
                <SnippetTypes>  
                    <SnippetType>Expansion</SnippetType>  
                </SnippetTypes>  
            </Header>  
            <Snippet>  
                <Declarations>  
                    <Literal>  
                      <ID>param1</ID>  
                        <ToolTip>First field</ToolTip>  
                        <Default>first</Default>  
                    </Literal>  
                    <Literal>  
                        <ID>param2</ID>  
                        <ToolTip>Second field</ToolTip>  
                        <Default>second</Default>  
                    </Literal>  
                </Declarations>  
                <References>  
                   <Reference>  
                       <Assembly>System.Windows.Forms.dll</Assembly>  
                   </Reference>  
                </References>  
                <Code Language="TestSnippets">  
                    <![CDATA[MessageBox.Show("$param1$");  
         MessageBox.Show("$param2$");]]>  
                </Code>    
            </Snippet>  
        </CodeSnippet>  
    </CodeSnippets>  
    ```  
  
 Poniższe kroki pokazują, jak zarejestrować wstawki kodu.  
  
#### <a name="to-register-code-snippets-for-a-specific-guid"></a>Aby zarejestrować wstawki kodu dla określonego identyfikatora GUID  
  
1.  Otwórz **CompletionTest** projektu. Aby uzyskać informacje o sposobie tworzenia tego projektu, zobacz [wskazówki: wyświetlanie uzupełniania](../extensibility/walkthrough-displaying-statement-completion.md).  
  
2.  W projekcie Dodaj odwołania do następujących zestawów:  
  
    -   Microsoft.VisualStudio.TextManager.Interop  
  
    -   Microsoft.VisualStudio.TextManager.Interop.8.0  
  
    -   Microsoft.MSXML  
  
3.  W projekcie Otwórz plik Source.Extension.vsixmanifest,a.  
  
4.  Upewnij się, że **zasoby** karta zawiera **pakiet VsPackage** zawartości typu i który **projektu** jest ustawiona na nazwę projektu.  
  
5.  Wybierz projekt CompletionTest i w oknie właściwości ustaw **Generowanie pliku Pkgdef** do **true**. Zapisz projekt.  
  
6.  Dodawanie statycznego `SnippetUtilities` klasy do projektu.  
  
     [!code-csharp[VSSDKCompletionTest#22](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_1.cs)]
     [!code-vb[VSSDKCompletionTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_1.vb)]  
  
7.  W klasie SnippetUtilities zdefiniować identyfikator GUID i nadaj mu wartość używana w pliku SnippetsIndex.xml.  
  
     [!code-csharp[VSSDKCompletionTest#23](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_2.cs)]
     [!code-vb[VSSDKCompletionTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_2.vb)]  
  
8.  Dodaj <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> do `TestCompletionHandler` klasy. Ten atrybut można dodać do każdej klasy publiczny lub wewnętrzny (niestatyczna) w projekcie. (Należy dodać `using` instrukcji dla przestrzeni nazw Microsoft.VisualStudio.Shell.)  
  
     [!code-csharp[VSSDKCompletionTest#24](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_3.cs)]
     [!code-vb[VSSDKCompletionTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_3.vb)]  
  
9. Tworzenie i uruchamianie projektu. W eksperymentalne wystąpienie programu Visual Studio, która rozpoczyna się po uruchomieniu projektu, fragment został zarejestrowany powinien być wyświetlany w **Menedżerze fragmentów kodu** w obszarze **TestSnippets** języka.  
  
## <a name="adding-the-insert-snippet-command-to-the-shortcut-menu"></a>Dodawanie polecenia fragment wstawiania do Menu skrótów  
 **Wstawić fragment** polecenia nie znajduje się w menu skrótów do pliku tekstowego. W związku z tym należy włączyć polecenia.  
  
#### <a name="to-add-the-insert-snippet-command-to-the-shortcut-menu"></a>Aby dodać polecenia Wstaw fragment do menu skrótów  
  
1.  Otwórz `TestCompletionCommandHandler` pliku klasy.  
  
     Ponieważ ta klasa implementuje <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>, można aktywować **wstawić fragment** polecenia w <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metody. Przed włączeniem polecenia, sprawdź, czy ta metoda nie jest wywoływana wewnątrz funkcji automatyzacji ponieważ podczas **wstawić fragment** polecenia zostanie kliknięty, będą wyświetlane fragment selektora interfejsu użytkownika (UI).  
  
     [!code-csharp[VSSDKCompletionTest#25](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_4.cs)]
     [!code-vb[VSSDKCompletionTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_4.vb)]  
  
2.  Tworzenie i uruchamianie projektu. W eksperymentalnym wystąpieniu Otwórz plik, który ma rozszerzenie nazwy pliku .zzz i kliknij prawym przyciskiem myszy dowolne miejsce w nim. **Wstawić fragment** polecenie powinno pojawić się w menu skrótów.  
  
## <a name="implementing-snippet-expansion-in-the-snippet-picker-ui"></a>Wdrażanie rozszerzenia fragment kodu w interfejsie użytkownika selektora fragment kodu  
 W tej sekcji przedstawiono sposób zaimplementować rozszerzenia fragment kodu, aby selektor wstawek interfejsu użytkownika jest wyświetlane, gdy **wstawić fragment** zostanie kliknięty menu skrótów. Fragment kodu jest również rozwinięty, gdy użytkownik wpisze skrótów fragmentu kodu i następnie naciska klawisz TAB.  
  
 Aby wyświetlić selektor wstawek interfejsu użytkownika i włączyć nawigacji i fragment wstawiania po zaakceptowaniu, należy użyć <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metody. Samo wstawienie jest obsługiwany przez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> metody.  
  
 Implementacja rozszerzenia fragment kodu używa starszego <xref:Microsoft.VisualStudio.TextManager.Interop> interfejsów. Podczas tłumaczenia z bieżącej klasy edytora kodu starszych należy pamiętać, że interfejsy starszej wersji należy zastosować kombinację numery wierszy i numery kolumn do określenia lokalizacji w buforze tekstu, ale jeden indeks użyć bieżącej klasy. W związku z tym jeśli bufor składa się z trzech wierszy, z których każda ma 10 znaków (oraz nowego wiersza, który jest traktowana jako 1 znak), jest czwarty znak na trzeci wiersz na pozycji 27 obecnej, ale jest w wierszu 2, umieść 3 w starym implementacji.  
  
#### <a name="to-implement-snippet-expansion"></a>Aby zaimplementować fragment rozszerzenia  
  
1.  Do pliku, który zawiera `TestCompletionCommandHandler` klasy, należy dodać następujące `using` instrukcje.  
  
     [!code-csharp[VSSDKCompletionTest#26](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_5.cs)]
     [!code-vb[VSSDKCompletionTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_5.vb)]  
  
2.  Wprowadź `TestCompletionCommandHandler` implementacji klasy <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> interfejsu.  
  
     [!code-csharp[VSSDKCompletionTest#27](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_6.cs)]
     [!code-vb[VSSDKCompletionTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_6.vb)]  
  
3.  W `TestCompletionCommandHandlerProvider` klasy, zaimportuj <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>.  
  
     [!code-csharp[VSSDKCompletionTest#28](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_7.cs)]
     [!code-vb[VSSDKCompletionTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_7.vb)]  
  
4.  Dodaj pola prywatne dla interfejsów rozszerzenia kodu i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.  
  
     [!code-csharp[VSSDKCompletionTest#29](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_8.cs)]
     [!code-vb[VSSDKCompletionTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_8.vb)]  
  
5.  W Konstruktorze `TestCompletionCommandHandler` klasy, ustaw następujące pola.  
  
     [!code-csharp[VSSDKCompletionTest#30](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_9.cs)]
     [!code-vb[VSSDKCompletionTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_9.vb)]  
  
6.  Aby wyświetlić selektor wstawek, gdy użytkownik kliknie **wstawić fragment** polecenia, Dodaj następujący kod do <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> — metoda. (Aby wyjaśnienie to był bardziej czytelny, nie jest wyświetlany kod Exec(), który służy do uzupełniania; zamiast tego bloki kodu są dodawane do istniejącej metody). Dodaj następujący blok kodu po kod, który sprawdza, czy znak.  
  
     [!code-csharp[VSSDKCompletionTest#31](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_10.cs)]
     [!code-vb[VSSDKCompletionTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_10.vb)]  
  
7.  Jeśli fragment ma pola, które mogą zostać przesłane, sesja rozszerzenia pozostaje otwarte do momentu rozszerzenie jawnie zaakceptowania; Jeśli fragment kodu nie ma pól, sesja zostanie zamknięte, a wartość jest zwracana jako `null` przez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A> metody. W <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metody po selektor wstawek kodu interfejsu użytkownika, który dodanym w poprzednim kroku, Dodaj następujący kod do obsługi nawigacji fragment (gdy użytkownik naciśnie klawisz TAB lub klawisze SHIFT + TAB po wstawieniu fragmentu).  
  
     [!code-csharp[VSSDKCompletionTest#32](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_11.cs)]
     [!code-vb[VSSDKCompletionTest#32](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_11.vb)]  
  
8.  Aby wstawić fragment kodu, gdy użytkownik typy odpowiedniego skrótu, a następnie naciska klawisz TAB, Dodaj kod, aby <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metody. Metoda prywatna, która wstawia fragment kodu będą wyświetlane w kolejnym kroku. Dodaj następujący kod po kodzie nawigacji, który został dodany w poprzednim kroku.  
  
     [!code-csharp[VSSDKCompletionTest#33](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_12.cs)]
     [!code-vb[VSSDKCompletionTest#33](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_12.vb)]  
  
9. Implementacja metod <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> interfejsu. W tej implementacji, są tylko metody odsetek <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A> i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>. Inne metody tylko powinien zwrócić <xref:Microsoft.VisualStudio.VSConstants.S_OK>.  
  
     [!code-csharp[VSSDKCompletionTest#34](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_13.cs)]
     [!code-vb[VSSDKCompletionTest#34](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_13.vb)]  
  
10. Implementowanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> metody. Metoda pomocnicza, która faktycznie wstawia rozszerzenia zostanie omówiona w ostatnim kroku. <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> Udostępnia informacje wierszy i kolumn, które można pobrać z <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.  
  
     [!code-csharp[VSSDKCompletionTest#35](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_14.cs)]
     [!code-vb[VSSDKCompletionTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_14.vb)]  
  
11. Następujące metody prywatnej wstawia fragment kodu, oparte na skrót lub nazwa i ścieżka. Następnie wywołuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A> metody za pomocą fragmentu.  
  
     [!code-csharp[VSSDKCompletionTest#36](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_15.cs)]
     [!code-vb[VSSDKCompletionTest#36](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_15.vb)]  
  
## <a name="building-and-testing-code-snippet-expansion"></a>Tworzenie i testowanie rozszerzenia wstawek kodu  
 Należy sprawdzić, czy działa fragment rozszerzeń w projekcie.  
  
1.  Skompiluj rozwiązanie. Po uruchomieniu tego projektu w debugerze, drugie wystąpienie programu Visual Studio zostanie uruchomiony.  
  
2.  Otwórz plik tekstowy i wpisz tekst.  
  
3.  Kliknij prawym przyciskiem myszy w dowolnym miejscu w tekście, a następnie kliknij przycisk **wstawić fragment**.  
  
4.  Selektor wstawek interfejsu użytkownika powinien zostać wyświetlony z wyświetla komunikat informujący o **zastępczy pola testowe**. Kliknij dwukrotnie oknie podręcznym.  
  
     Należy dodać następujący fragment kodu.  
  
    ```  
    MessageBox.Show("first");  
    MessageBox.Show("second");  
    ```  
  
     Nie naciśnij ENTER lub ESC.  
  
5.  Naciśnij klawisz TAB lub klawisze SHIFT + TAB, aby przełączyć między "pierwszy" i "drugi".  
  
6.  Zaakceptuj wstawiania, naciskając klawisz ENTER lub ESC.  
  
7.  W innej części tekstu wpisz "test", a następnie naciśnij klawisz TAB. Ponieważ "test" jest skrót fragment kodu, fragment powinien zostać wstawiony ponownie.  
  
## <a name="next-steps"></a>Następne kroki