---
title: "Wskazówki: Wyświetlanie pomocy podpisu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - signature help/parameter info
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
caps.latest.revision: "28"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ced0eb5d3545a75ee31cff55d0e4fb9dab8c8bcb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-displaying-signature-help"></a>Wskazówki: Wyświetlanie pomocy podpisu
Podpis pomocy (znanej także jako *informacje o parametrach*) wyświetlany w etykietce narzędzia podpis metody, gdy użytkownik wpisze znak start listy parametrów (zazwyczaj nawias otwierający). Trakcie wpisywania parametru i parametr separatora (zazwyczaj przecinkami), element tooltip jest aktualizowana w celu wyświetlenia następny parametr pogrubione. Podpis pomocy można zdefiniować w kontekście usługi języka, można zdefiniować własny plik Nazwa rozszerzenia i zawartości typu i wyświetlić Pomoc podpisu dla właśnie tego typu lub można wyświetlić pomocy podpisu dla istniejącego typu zawartości (na przykład "tekst"). Ten przewodnik przedstawia sposób wyświetlenia pomocy podpisu dla typu zawartości "text".  
  
 Podpis pomocy zwykle jest wyzwalany przez wpisanie określonych znaków, na przykład "(" (nawias otwierający), a zostanie odrzucony, wpisując znak inny, na przykład ")" (nawiasy zamykające). Funkcje IntelliSense, które są uruchamiane, wpisując znak można zaimplementować przy użyciu programu obsługi poleceń dla naciśnięcia klawiszy ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface) i dostawcy programu obsługi, który implementuje <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> interfejsu. Można utworzyć źródła pomocy podpisu, czyli listy podpisów uczestniczących w pomocy podpis implementacji <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> interfejsu i dostawcy źródłowego, który implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> interfejsu. Dostawcy są składnikami Managed Extensibility Framework (MEF) i są odpowiedzialne za eksportowanie klas źródła i kontrolera i importowanie usług i brokerów, na przykład <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, pozwalającej przejdź do buforu tekstu i <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>, który wyzwala sesji pomocy podpisu.  
  
 W tym przewodniku pokazano, jak zaimplementować pomocy podpisu ustalony zbiór identyfikatorów. W pełnej implementacji język jest odpowiedzialny za zapewnienie tej zawartości.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, użytkownik nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest uwzględniona jako opcjonalna funkcja w Instalatorze programu Visual Studio. Można także zainstalować zestawu SDK dla programu późniejsze. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Tworzenie projektu MEF  
  
#### <a name="to-create-a-mef-project"></a>Aby utworzyć projekt MEF  
  
1.  Tworzenie projektu C# VSIX. (W **nowy projekt** okno dialogowe, wybierz opcję **Visual C# / rozszerzalności**, następnie **projektu VSIX**.) Nazwa rozwiązania `SignatureHelpTest`.  
  
2.  Dodaj szablon elementu klasyfikatora edytora do projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia z szablonem elementu edytor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Usuń pliki istniejące klasy.  
  
4.  Dodaj następujące odwołania do projektu i upewnij się, że **CopyLocal** ma ustawioną wartość `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## <a name="implementing-signature-help-signatures-and-parameters"></a>Implementowanie podpisu podpisów i parametry  
 Źródło pomocy podpis jest oparta na podpisów, które implementują <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>, z których każdy zawiera parametry, które implementują <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>. W pełnej implementacji tych informacji będzie można uzyskać z dokumentację języka, ale w tym przykładzie podpisy są zakodowane na stałe.  
  
#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>Aby zaimplementować podpisy pomocy podpisu i parametry  
  
1.  Dodaj plik klasy i nadaj mu nazwę `SignatureHelpSource`.  
  
2.  Dodaj następujące instrukcje importu.  
  
     [!code-vb[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_1.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_1.cs)]  
  
3.  Dodaj klasę o nazwie `TestParameter` implementującej <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.  
  
     [!code-vb[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_2.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_2.cs)]  
  
4.  Dodaj Konstruktor, który ustawia wszystkie właściwości.  
  
     [!code-vb[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_3.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_3.cs)]  
  
5.  Dodaj właściwości <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.  
  
     [!code-vb[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_4.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_4.cs)]  
  
6.  Dodaj klasę o nazwie `TestSignature` implementującej <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>.  
  
     [!code-vb[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_5.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_5.cs)]  
  
7.  Dodać niektórych pól prywatnych.  
  
     [!code-vb[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_6.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_6.cs)]  
  
8.  Dodaj Konstruktor, który ustawia pola i subskrybuje <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> zdarzeń.  
  
     [!code-vb[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_7.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_7.cs)]  
  
9. Deklarowanie `CurrentParameterChanged` zdarzeń. To zdarzenie jest wywoływane, gdy użytkownik wpisuje do jednego z parametrów w podpisie.  
  
     [!code-vb[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_8.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_8.cs)]  
  
10. Implementowanie <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> właściwości, tak że zgłasza `CurrentParameterChanged` zdarzenie, gdy wartość właściwości zostanie zmieniona.  
  
     [!code-vb[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_9.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_9.cs)]  
  
11. Dodaj metodę, który wywołuje `CurrentParameterChanged` zdarzeń.  
  
     [!code-vb[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_10.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_10.cs)]  
  
12. Dodaj metodę, która oblicza bieżącego parametru przez porównanie liczby przecinków w <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> liczby przecinkami w podpisie.  
  
     [!code-vb[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_11.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_11.cs)]  
  
13. Dodaj program obsługi zdarzeń dla <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> zdarzeń, który wywołuje `ComputeCurrentParameter()` metody.  
  
     [!code-vb[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_12.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_12.cs)]  
  
14. Implementowanie <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> właściwości. Ta właściwość przechowuje <xref:Microsoft.VisualStudio.Text.ITrackingSpan> odpowiadający zakres tekstu w buforze, którego dotyczy podpisu.  
  
     [!code-vb[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_13.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_13.cs)]  
  
15. Implementuje innych parametrów.  
  
     [!code-vb[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_14.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_14.cs)]  
  
## <a name="implementing-the-signature-help-source"></a>Implementowanie źródłowego pomocy podpisu  
 Źródło pomocy podpis jest zestaw podpisów, dla których należy podać informacje.  
  
#### <a name="to-implement-the-signature-help-source"></a>Aby zaimplementować źródła pomocy podpisu  
  
1.  Dodaj klasę o nazwie `TestSignatureHelpSource` implementującej <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>.  
  
     [!code-vb[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_15.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_15.cs)]  
  
2.  Dodaj odwołanie do buforu tekstu.  
  
     [!code-vb[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_16.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_16.cs)]  
  
3.  Dodaj Konstruktor, który ustawia bufor tekstowy i dostawca źródła pomocy podpisu.  
  
     [!code-vb[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_17.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_17.cs)]  
  
4.  Implementowanie <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A> metody. W tym przykładzie podpisy są zakodowane na stałe, ale w pełnej implementacji jak te informacje w dokumentacji języka.  
  
     [!code-vb[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_18.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_18.cs)]  
  
5.  Metoda pomocnicza `CreateSignature()` podano tylko do celów informacyjnych.  
  
     [!code-vb[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_19.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_19.cs)]  
  
6.  Implementowanie <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A> metody. W tym przykładzie istnieją tylko dwa podpisów, z których każdy zawiera dwa parametry. W związku z tym ta metoda nie jest wymagane. W pełniejsze implementacji, w której więcej niż jedno źródło podpisu pomocy jest dostępny, ta metoda służy do określania, czy źródła pomocy podpisu najwyższy priorytet można podać zgodnego podpisu. Jeśli nie, metoda zwraca wartość null i źródła dalej najwyższym priorytecie jest monitowany o podanie dopasowania.  
  
     [!code-vb[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_20.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_20.cs)]  
  
7.  Implementacja metody Dispose():  
  
     [!code-vb[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_21.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_21.cs)]  
  
## <a name="implementing-the-signature-help-source-provider"></a>Implementowanie dostawcy źródła pomocy podpisu  
 Dostawca źródła pomocy podpisu jest odpowiedzialny za eksportowanie część składnika Managed Extensibility Framework (MEF) i tworzenie wystąpień źródła pomocy podpisu.  
  
#### <a name="to-implement-the-signature-help-source-provider"></a>Do implementowania dostawcy źródła pomocy podpisu  
  
1.  Dodaj klasę o nazwie `TestSignatureHelpSourceProvider` implementującej <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>i wyeksportować go przy użyciu <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> z "text" i <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> z przed = "default".  
  
     [!code-vb[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_22.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_22.cs)]  
  
2.  Implementowanie <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> przez utworzenie wystąpienia `TestSignatureHelpSource`.  
  
     [!code-vb[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_23.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_23.cs)]  
  
## <a name="implementing-the-command-handler"></a>Implementacja programu obsługi poleceń  
 Podpis pomocy zwykle jest wyzwalany przez (znak i odrzucony przez) znaków. Może obsłużyć naciśnięcia zaimplementowanie <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> tak, aby wyzwala sesji pomocy podpisu po otrzymaniu (znak poprzedzony przez nazwę metody znanych i odrzuci sesji, gdy odbierze ona) znaków.  
  
#### <a name="to-implement-the-command-handler"></a>Aby zaimplementować program obsługi poleceń  
  
1.  Dodaj klasę o nazwie `TestSignatureHelpCommand` implementującej <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
     [!code-vb[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_24.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_24.cs)]  
  
2.  Dodać pól prywatnych dla <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> karty (który umożliwia dodanie program obsługi poleceń do obsługi podporządkowania), widoku tekstu, broker pomocy podpisu i sesji, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>, następna <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
     [!code-vb[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_25.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_25.cs)]  
  
3.  Dodaj Konstruktor zainicjować te pola i aby dodać filtr polecenia do filtrów służbowej.  
  
     [!code-vb[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_26.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_26.cs)]  
  
4.  Wdrożenie <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodę, aby wyzwolić pomocy podpisu sesji, gdy odbierze polecenie filtru (znak po jednej z nazwy metod znanych oraz aby odrzucić sesji, gdy odbierze ona) znaków podczas sesji jest nadal aktywne. W każdym przypadku polecenia są przesyłane dalej.  
  
     [!code-vb[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_27.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_27.cs)]  
  
5.  Implementowanie <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodę, tak aby zawsze przekazuje polecenia.  
  
     [!code-vb[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_28.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_28.cs)]  
  
## <a name="implementing-the-signature-help-command-provider"></a>Implementowanie dostawcy polecenia pomocy podpisu  
 Zapewniają polecenia Pomoc podpisu zaimplementowanie <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> można utworzyć wystąpienia programu obsługi poleceń podczas tworzenia widoku tekstu.  
  
#### <a name="to-implement-the-signature-help-command-provider"></a>Do implementowania dostawcy polecenia pomocy podpisu  
  
1.  Dodaj klasę o nazwie `TestSignatureHelpController` implementującej <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> i wyeksportować go przy użyciu <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>, i <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>.  
  
     [!code-vb[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_29.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_29.cs)]  
  
2.  Importuj <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> (używany do pobierania <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, używając podanych <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> obiektu), <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> (używana do znajdowania bieżącego słowa) i <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> (Aby wyzwolić sesji pomocy podpis).  
  
     [!code-vb[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_30.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_30.cs)]  
  
3.  Implementowanie <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> metody przez utworzenie wystąpienia `TestSignatureCommandHandler`.  
  
     [!code-vb[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_31.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_31.cs)]  
  
## <a name="building-and-testing-the-code"></a>Tworzenie i testowanie kodu  
 Do przetestowania tego kodu, Skompiluj rozwiązanie SignatureHelpTest i uruchom go w eksperymentalnym wystąpieniu.  
  
#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>Tworzenie i testowanie rozwiązania SignatureHelpTest  
  
1.  Skompiluj rozwiązanie.  
  
2.  Po uruchomieniu tego projektu w debugerze, drugie wystąpienie programu Visual Studio zostanie uruchomiony.  
  
3.  Utwórz plik tekstowy i wpisz tekst, który zawiera słowo "Dodaj" oraz nawias otwierający.  
  
4.  Po wpisaniu nawias otwierający powinna zostać wyświetlona etykietka narzędzia, który wyświetla listę dwóch sygnatury `add()` metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: łączenie typu zawartości z rozszerzeniem nazwy pliku](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)