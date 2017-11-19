---
title: "Wskazówki: Wyświetlanie uzupełniania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - statement completion
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
caps.latest.revision: "36"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7ebdc87e1dccf2bde66ccfeebb6c2b4fba144c70
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-displaying-statement-completion"></a>Wskazówki: Wyświetlanie uzupełniania
Uzupełnianie opartych na języku można zaimplementować definiujący identyfikatory, dla których chcesz podać ukończenia, a następnie wyzwalania zakończenia sesji. Można zdefiniować uzupełniania w kontekście usługi języka, definiować własne rozszerzenie nazwy pliku i typu zawartości i Wyświetl uzupełnianie tylko tego typu lub możesz wyzwolić uzupełnianie istniejącego typu zawartości — na przykład "w postaci zwykłego tekstu". W tym przewodniku przedstawiono sposób wyzwolenia uzupełniania dla typu zawartości "zwykły tekst", który jest typem zawartości plików tekstowych. Typ zawartości "text" jest elementem nadrzędnym wszystkich innych typów zawartości, łącznie z kodu i pliki XML.  
  
 Uzupełnianie zwykle jest wyzwalany przez wpisanie określonych znaków — na przykład, wpisując początek identyfikatora, takie jak "using". Jest on zwykle odrzucane naciskając klawisz spacji, tabulatorem ani Enter można przekazać zaznaczenia. Można zaimplementować funkcji IntelliSense, które są uruchamiane, wpisując znak przy użyciu programu obsługi poleceń dla naciśnięcia klawiszy ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface) i dostawcy programu obsługi, który implementuje <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> interfejsu. Aby utworzyć źródło zakończenia, w którym znajduje się lista identyfikatorów należące do ukończenia, zaimplementuj <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> interfejsu i dostawca źródła zakończenia ( <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> interfejs). Dostawców są składnikami Managed Extensibility Framework (MEF). Są odpowiedzialne za eksportowanie klas źródła i kontrolera i importowanie usług, a brokerzy — na przykład <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, które umożliwia nawigacji w buforze tekstu i <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>, który wyzwala zakończenia sesji.  
  
 W tym przewodniku pokazano, jak zaimplementować uzupełniania ustalony zbiór identyfikatorów. W pełnej implementacji usługi języka oraz dokumentację języka spoczywa odpowiedzialność za zapewnienie tej zawartości.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, użytkownik nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest uwzględniona jako opcjonalna funkcja w Instalatorze programu Visual Studio. Można także zainstalować zestawu SDK dla programu późniejsze. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Tworzenie projektu MEF  
  
#### <a name="to-create-a-mef-project"></a>Aby utworzyć projekt MEF  
  
1.  Tworzenie projektu C# VSIX. (W **nowy projekt** okno dialogowe, wybierz opcję **Visual C# / rozszerzalności**, następnie **projektu VSIX**.) Nazwa rozwiązania `CompletionTest`.  
  
2.  Dodaj szablon elementu klasyfikatora edytora do projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia z szablonem elementu edytor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Usuń pliki istniejące klasy.  
  
4.  Dodaj następujące odwołania do projektu i upewnij się, że **CopyLocal** ma ustawioną wartość `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.Shell.Immutable.10.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## <a name="implementing-the-completion-source"></a>Implementowanie źródłowego uzupełniania  
 Źródło zakończenia jest odpowiedzialny za zbieranie zestaw identyfikatorów i dodawanie zawartości do zakończenia okna, gdy użytkownik wpisze wyzwalacz ukończenia, takie jak pierwsze litery identyfikatora. W tym przykładzie identyfikatorów i ich opisy są zakodowane na stałe w <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> metody. W większości rzeczywistych zastosowaniach należy użyć analizatora swój język uzyskać tokenów do wypełnienia listy uzupełniania.  
  
#### <a name="to-implement-the-completion-source"></a>Aby zaimplementować źródła uzupełniania  
  
1.  Dodaj plik klasy i nadaj mu nazwę `TestCompletionSource`.  
  
2.  Dodaj te importów:  
  
     [!code-csharp[VSSDKCompletionTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_1.cs)]
     [!code-vb[VSSDKCompletionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_1.vb)]  
  
3.  Modyfikowanie deklaracja klasy `TestCompletionSource` tak, aby ją implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>:  
  
     [!code-csharp[VSSDKCompletionTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_2.cs)]
     [!code-vb[VSSDKCompletionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_2.vb)]  
  
4.  Dodać pól prywatnych dla dostawcy źródła, buforu tekstu oraz listę <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> obiektów (które odnoszą się do identyfikatorów, które będą uczestniczyć w sesji ukończenia):  
  
     [!code-csharp[VSSDKCompletionTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_3.cs)]
     [!code-vb[VSSDKCompletionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_3.vb)]  
  
5.  Dodaj Konstruktor, który Ustawia dostawcę źródła i buforu. `TestCompletionSourceProvider` Klasa jest zdefiniowana w kolejnych krokach:  
  
     [!code-csharp[VSSDKCompletionTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_4.cs)]
     [!code-vb[VSSDKCompletionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_4.vb)]  
  
6.  Implementowanie <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> metody przez dodanie zestaw zakończenia, który zawiera zakończeń ma być dostępny w tym kontekście. Każdy zestaw zakończenia zawiera zbiór <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> zakończeń i odpowiada na karcie okna ukończenia. (W projektach Visual Basic, o nazwie karty okna ukończenia **typowe** i **wszystkie**.) Metoda FindTokenSpanAtPosition jest zdefiniowana w następnym kroku.  
  
     [!code-csharp[VSSDKCompletionTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_5.cs)]
     [!code-vb[VSSDKCompletionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_5.vb)]  
  
7.  Następująca metoda jest używana do znajdowania bieżącego słowa od pozycji kursora:  
  
     [!code-csharp[VSSDKCompletionTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_6.cs)]
     [!code-vb[VSSDKCompletionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_6.vb)]  
  
8.  Implementowanie `Dispose()` metody:  
  
     [!code-csharp[VSSDKCompletionTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_7.cs)]
     [!code-vb[VSSDKCompletionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_7.vb)]  
  
## <a name="implementing-the-completion-source-provider"></a>Implementowanie dostawcy źródła uzupełniania  
 Dostawca źródła zakończenia jest części składników MEF tworzącym źródła ukończenia.  
  
#### <a name="to-implement-the-completion-source-provider"></a>Aby zaimplementować dostawcę źródła zakończenia  
  
1.  Dodaj klasę o nazwie `TestCompletionSourceProvider` implementującej <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>. Eksportuj tę klasę z <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "zwykłego tekstu" i <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "wykonania testu".  
  
     [!code-csharp[VSSDKCompletionTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_8.cs)]
     [!code-vb[VSSDKCompletionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_8.vb)]  
  
2.  Importuj <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, która jest używana do znajdowania bieżącego słowa w źródle ukończenia.  
  
     [!code-csharp[VSSDKCompletionTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_9.cs)]
     [!code-vb[VSSDKCompletionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_9.vb)]  
  
3.  Implementowanie <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> metody tworzenia wystąpienia źródła ukończenia.  
  
     [!code-csharp[VSSDKCompletionTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_10.cs)]
     [!code-vb[VSSDKCompletionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_10.vb)]  
  
## <a name="implementing-the-completion-command-handler-provider"></a>Implementowanie dostawcy obsługi polecenie zakończenia  
 Dostawca obsługi polecenie zakończenia jest pochodną <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>, która wykrywa zdarzenie tworzenia widoku tekstu i konwertuje widoku z <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>— umożliwiające dodanie polecenia w łańcuchu polecenia powłoki programu Visual Studio — do <xref:Microsoft.VisualStudio.Text.Editor.ITextView>. Ponieważ ta klasa jest eksportu MEF, umożliwia także go zaimportować usług, które są wymagane przez sam program obsługi poleceń.  
  
#### <a name="to-implement-the-completion-command-handler-provider"></a>Do implementowania dostawcy obsługi polecenie zakończenia  
  
1.  Dodaj plik o nazwie `TestCompletionCommandHandler`.  
  
2.  Dodaj te instrukcje using:  
  
     [!code-csharp[VSSDKCompletionTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_11.cs)]
     [!code-vb[VSSDKCompletionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_11.vb)]  
  
3.  Dodaj klasę o nazwie `TestCompletionHandlerProvider` implementującej <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>. Eksportuj tej klasy z <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "programu obsługi zakończenia tokenu", <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "zwykłego tekstu", a <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> z <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable>.  
  
     [!code-csharp[VSSDKCompletionTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_12.cs)]
     [!code-vb[VSSDKCompletionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_12.vb)]  
  
4.  Import <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>, które umożliwia konwersję z <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> do <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>, a <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> , umożliwia dostęp do usług w warstwie standardowa Visual Studio.  
  
     [!code-csharp[VSSDKCompletionTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_13.cs)]
     [!code-vb[VSSDKCompletionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_13.vb)]  
  
5.  Implementowanie <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> metody można utworzyć wystąpienia programu obsługi poleceń.  
  
     [!code-csharp[VSSDKCompletionTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_14.cs)]
     [!code-vb[VSSDKCompletionTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_14.vb)]  
  
## <a name="implementing-the-completion-command-handler"></a>Implementacja programu obsługi poleceń uzupełniania  
 Ponieważ uzupełniania jest wyzwalany przez naciśnięcia klawiszy, musisz zaimplementować <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu odbierały i przetwarzały naciśnięcia klawiszy, które wyzwalania, zatwierdzenia i odrzucić zakończenia sesji.  
  
#### <a name="to-implement-the-completion-command-handler"></a>Aby zaimplementować program obsługi poleceń uzupełniania  
  
1.  Dodaj klasę o nazwie `TestCompletionCommandHandler` implementującej <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:  
  
     [!code-csharp[VSSDKCompletionTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_15.cs)]
     [!code-vb[VSSDKCompletionTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_15.vb)]  
  
2.  Dodać pól prywatnych dalej program obsługi poleceń (do którego należy przekazać polecenie), widoku tekstu, Dostawca obsługi polecenie (który umożliwia dostęp do różnych usług) i zakończenie sesji:  
  
     [!code-csharp[VSSDKCompletionTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_16.cs)]
     [!code-vb[VSSDKCompletionTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_16.vb)]  
  
3.  Dodaj konstruktora, który ustawia widoku tekstu i pola dostawcy i dodaje polecenia do łańcucha polecenia:  
  
     [!code-csharp[VSSDKCompletionTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_17.cs)]
     [!code-vb[VSSDKCompletionTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_17.vb)]  
  
4.  Implementowanie <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metody przez przekazanie polecenia wzdłuż:  
  
     [!code-csharp[VSSDKCompletionTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_18.cs)]
     [!code-vb[VSSDKCompletionTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_18.vb)]  
  
5.  Implementowanie <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metody. Gdy ta metoda odbiera naciśnięcia klawisza, wykonaj jedną z tych czynności:  
  
    -   Zezwalaj na znak można zapisać w buforze i następnie wyzwalacza lub Filtruj ukończenia. (Drukowanie znaków w tym.)  
  
    -   Zatwierdź zakończenia, ale nie zezwalaj na znak do zapisania w buforze. (Spacji, karta i wprowadź w tym wyświetlania zakończenia sesji.)  
  
    -   Zezwalaj na polecenie, aby być przekazywane do następnej procedury obsługi. (Wszystkie inne polecenia.)  
  
     Ponieważ ta metoda może wyświetlać interfejsu użytkownika, należy wywołać <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> aby upewnić się, że nie jest wywoływana w kontekście automatyzacji:  
  
     [!code-csharp[VSSDKCompletionTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_19.cs)]
     [!code-vb[VSSDKCompletionTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_19.vb)]  
  
6.  Ten kod jest metody prywatnej, która wyzwala zakończenia sesji:  
  
     [!code-csharp[VSSDKCompletionTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_20.cs)]
     [!code-vb[VSSDKCompletionTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_20.vb)]  
  
7.  Kolejnym przykładzie jest metody prywatnej, która cofnięć subskrypcji z <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> zdarzeń:  
  
     [!code-csharp[VSSDKCompletionTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_21.cs)]
     [!code-vb[VSSDKCompletionTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_21.vb)]  
  
## <a name="building-and-testing-the-code"></a>Tworzenie i testowanie kodu  
 Do przetestowania tego kodu, Skompiluj rozwiązanie CompletionTest i uruchom go w eksperymentalnym wystąpieniu.  
  
#### <a name="to-build-and-test-the-completiontest-solution"></a>Tworzenie i testowanie rozwiązania CompletionTest  
  
1.  Skompiluj rozwiązanie.  
  
2.  Po uruchomieniu tego projektu w debugerze, drugie wystąpienie programu Visual Studio zostanie uruchomiony.  
  
3.  Utwórz plik tekstowy i wpisz tekst, który zawiera słowo "Dodaj".  
  
4.  Podczas wpisywania najpierw "a", a następnie "d" powinna być wyświetlana lista zawierająca "Dodawanie" i "dostosowania". Zwróć uwagę, że wybrany jest dodanie. Po wpisaniu "d" Lista powinna zawierać tylko "Dodawanie", który jest obecnie wybrany. Zatwierdzenia "Dodawanie" naciskając klawisz spacji, tabulatorem ani Enter lub odrzucić listy, wpisując Esc lub innego klucza.  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Łączenie typu zawartości z rozszerzeniem nazwy pliku](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)