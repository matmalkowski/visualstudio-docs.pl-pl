---
title: 'Wskazówki: Tworzenie symbolu margines | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 811985ef45fb43b08b771f2bc417a512c290726c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31142633"
---
# <a name="walkthrough-creating-a-margin-glyph"></a>Wskazówki: Tworzenie symbolu margines
Można dostosować wygląd marginesu edytora przy użyciu rozszerzenia niestandardowego edytora. W tym przewodniku umieszcza niestandardowych symbolu margines wskaźnika zawsze, gdy pojawi się w komentarz do kodu słowo "todo".  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, użytkownik nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest uwzględniona jako opcjonalna funkcja w Instalatorze programu Visual Studio. Można także zainstalować zestawu SDK dla programu późniejsze. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Tworzenie projektu MEF  
  
1.  Tworzenie projektu C# VSIX. (W **nowy projekt** okno dialogowe, wybierz opcję **Visual C# / rozszerzalności**, następnie **projektu VSIX**.) Nazwa rozwiązania `TodoGlyphTest`.  
  
2.  Dodawanie elementu projektu klasyfikatora edytora. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia z szablonem elementu edytor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Usuń pliki istniejące klasy.  
  
## <a name="defining-the-glyph"></a>Definiowanie symbolu  
 Zdefiniuj symbol zaimplementowanie <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> interfejsu.  
  
#### <a name="to-define-the-glyph"></a>Aby zdefiniować symbolu  
  
1.  Dodaj plik klasy i nadaj mu nazwę `TodoGlyphFactory`.  
  
2.  Dodaj następujący kod za pomocą deklaracji.  
  
     [!code-csharp[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_1.cs)]
     [!code-vb[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_1.vb)]  
  
3.  Dodaj klasę o nazwie `TodoGlyphFactory` implementującej <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>.  
  
     [!code-csharp[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_2.cs)]
     [!code-vb[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_2.vb)]  
  
4.  Dodaj pole prywatne, który definiuje wymiary symbolu.  
  
     [!code-csharp[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_3.cs)]
     [!code-vb[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_3.vb)]  
  
5.  Implementowanie `GenerateGlyph` , definiując elementu interfejsu użytkownika w obrębie symboli. `TodoTag` jest zdefiniowany w dalszej części tego przewodnika.  
  
     [!code-csharp[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_4.cs)]
     [!code-vb[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_4.vb)]  
  
6.  Dodaj klasę o nazwie `TodoGlyphFactoryProvider` implementującej <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider>. Eksportuj tej klasy z <xref:Microsoft.VisualStudio.Utilities.NameAttribute> z "TodoGlyph" <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> z VsTextMarker po <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Code", a <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> z TodoTag.  
  
     [!code-csharp[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_5.cs)]
     [!code-vb[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_5.vb)]  
  
7.  Implementowanie <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> metody przez utworzenie wystąpienia `TodoGlyphFactory`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_6.cs)]
     [!code-vb[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_6.vb)]  
  
## <a name="defining-a-todo-tag-and-tagger"></a>Definiowanie tagów Todo i modułu znakowania  
 Definiowania relacji między elementu interfejsu użytkownika, który został zdefiniowany w poprzednich krokach i wskaźnik marginesu tworzenia typ znacznika i modułu znakowania i eksportowanie go przy użyciu dostawcy modułu znakowania.  
  
#### <a name="to-define-a-todo-tag-and-tagger"></a>Aby zdefiniować tagów todo i modułu znakowania  
  
1.  Dodaj nowy plik klasy do projektu i nadaj mu nazwę `TodoTagger`.  
  
2.  Dodaj następujące instrukcje importu.  
  
     [!code-csharp[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_7.cs)]
     [!code-vb[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_7.vb)]  
  
3.  Dodaj klasę o nazwie `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_8.cs)]
     [!code-vb[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_8.vb)]  
  
4.  Modyfikowanie klasy o nazwie `TodoTagger` implementującej <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> typu `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_9.cs)]
     [!code-vb[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_9.vb)]  
  
5.  Aby `TodoTagger` klasy, dodać pól prywatnych dla <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> i na tekst do wyszukania w klasyfikacji, które obejmuje.  
  
     [!code-csharp[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_10.cs)]
     [!code-vb[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_10.vb)]  
  
6.  Dodaj Konstruktor, który ustawia klasyfikatora.  
  
     [!code-csharp[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_11.cs)]
     [!code-vb[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_11.vb)]  
  
7.  Implementowanie <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> metody znajdując dla klasyfikacji obejmuje których nazwy Dołącz słowo "comment" i którego tekstu zawiera tekst wyszukiwania. Zawsze, gdy zostanie znaleziony tekst do wyszukania, uzyskanie ponownie nowy <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> typu `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_12.cs)]
     [!code-vb[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_12.vb)]  
  
8.  Deklarowanie `TagsChanged` zdarzeń.  
  
     [!code-csharp[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_13.cs)]
     [!code-vb[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_13.vb)]  
  
9. Dodaj klasę o nazwie `TodoTaggerProvider` implementującej <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>i wyeksportować go przy użyciu <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Code" i <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> z TodoTag.  
  
     [!code-csharp[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_14.cs)]
     [!code-vb[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_14.vb)]  
  
10. Importuj <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>.  
  
     [!code-csharp[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_15.cs)]
     [!code-vb[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_15.vb)]  
  
11. Implementowanie <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> metody przez utworzenie wystąpienia `TodoTagger`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_16.cs)]
     [!code-vb[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_16.vb)]  
  
## <a name="building-and-testing-the-code"></a>Tworzenie i testowanie kodu  
 Do przetestowania tego kodu, Skompiluj rozwiązanie TodoGlyphTest i uruchom go w eksperymentalnym wystąpieniu.  
  
#### <a name="to-build-and-test-the-todoglyphtest-solution"></a>Tworzenie i testowanie rozwiązania TodoGlyphTest  
  
1.  Skompiluj rozwiązanie.  
  
2.  Uruchom projekt, naciskając klawisz F5. Drugie wystąpienie programu Visual Studio zostanie uruchomiony.  
  
3.  Upewnij się, że jest wyświetlany wskaźnik marginesu. (Na **narzędzia** menu, kliknij przycisk **opcje**. Na **Edytor tekstu** strony, upewnij się, że **wskaźnik marginesu** wybrano.)  
  
4.  Otwórz plik kodu, który ma komentarze. Dodaj ten wyraz "todo" do jednej z sekcji komentarza.  
  
5.  Światła niebieski okrąg ma ciemny konspektu niebieski powinny być wyświetlane w margines wskaźnika z lewej strony okna kodu.