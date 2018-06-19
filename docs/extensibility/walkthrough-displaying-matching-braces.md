---
title: 'Wskazówki: Wyświetlanie pasujących nawiasów klamrowych | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 370340246cd75e53580d1ac2b6c591f0854cb23e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31143322"
---
# <a name="walkthrough-displaying-matching-braces"></a>Wskazówki: Wyświetlanie pasujących nawiasów klamrowych
Można zaimplementować opartych na języku funkcje, takie jak parowanie nawiasów klamrowych Definiowanie nawiasów klamrowych, które chcesz dopasować, a następnie dodaniu tekstu znacznika do pasujących nawiasów klamrowych podczas karetka znajduje się na jednym z nawiasy klamrowe. Można zdefiniować nawiasy klamrowe w kontekście języka, można zdefiniować własny plik Nazwa rozszerzenia i zawartości typu i dotyczą tagi tylko tego typu lub tagów można zastosować do istniejącego typu zawartości (na przykład "tekst"). Poniższe wskazówki pokazano, jak zastosować parowanie nawiasów klamrowych znaczniki, aby typ zawartości "text".  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, użytkownik nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest uwzględniona jako opcjonalna funkcja w Instalatorze programu Visual Studio. Można także zainstalować zestawu SDK dla programu późniejsze. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Tworzenie projektu Framework (MEF) zarządzanych rozszerzeń  
  
#### <a name="to-create-a-mef-project"></a>Aby utworzyć projekt MEF  
  
1.  Tworzenie projektu klasyfikatora edytora. Nazwa rozwiązania `BraceMatchingTest`.  
  
2.  Dodaj szablon elementu klasyfikatora edytora do projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia z szablonem elementu edytor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Usuń pliki istniejące klasy.  
  
## <a name="implementing-a-brace-matching-tagger"></a>Implementowanie parowanie nawiasów klamrowych modułu znakowania  
 Aby uzyskać nawiasu klamrowego wyróżnianie efekt zbliżony do używanego w programie Visual Studio, można zaimplementować modułu znakowania typu <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>. Poniższy kod przedstawia sposób definiowania modułu znakowania par nawiasu klamrowego na dowolnym poziomie zagnieżdżenia. W tym przykładzie nawiasem pary []. [] {} są zdefiniowane w Konstruktorze modułu znakowania, ale w implementacji pełną obsługą języka pary odpowiednich nawiasu klamrowego byłoby zdefiniowane w specyfikacji języka.  
  
#### <a name="to-implement-a-brace-matching-tagger"></a>Aby zaimplementować parowanie nawiasów klamrowych modułu znakowania  
  
1.  Dodaj plik klasy i nadaj mu nazwę BraceMatching.  
  
2.  Importuj następujących przestrzeni nazw.  
  
     [!code-csharp[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_1.cs)]
     [!code-vb[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_1.vb)]  
  
3.  Zdefiniuj klasę `BraceMatchingTagger` dziedziczący po <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> typu <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.  
  
     [!code-csharp[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_2.cs)]
     [!code-vb[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_2.vb)]  
  
4.  Dodaj właściwości widoku tekstu, bufor źródłowy bieżącego punktu migawki i również zestaw par nawiasu klamrowego.  
  
     [!code-csharp[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_3.cs)]
     [!code-vb[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_3.vb)]  
  
5.  W Konstruktorze modułu znakowania Ustaw właściwości i subskrybowanie zdarzeń zmiany widoku <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> i <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>. W tym przykładzie do celów ilustracyjnych pasujących par można zdefiniować w konstruktorze.  
  
     [!code-csharp[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_4.cs)]
     [!code-vb[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_4.vb)]  
  
6.  W ramach <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> implementacji zadeklarować zdarzenia TagsChanged.  
  
     [!code-csharp[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_5.cs)]
     [!code-vb[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_5.vb)]  
  
7.  Programy obsługi zdarzeń aktualizacji bieżącym położeniu karetki `CurrentChar` właściwości i zgłoś TagsChanged zdarzeń.  
  
     [!code-csharp[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_6.cs)]
     [!code-vb[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_6.vb)]  
  
8.  Implementowanie <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> metody do dopasowania nawiasy klamrowe albo jeśli bieżący znak otwierający nawias klamrowy, lub gdy poprzedni znak jest Zamknij nawiasu klamrowego, jak w programie Visual Studio. Po znalezieniu dopasowania, ta metoda tworzy dwa tagi, jeden dla otwierający nawias klamrowy i jeden dla Zamknij nawiasu klamrowego.  
  
     [!code-csharp[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_7.cs)]
     [!code-vb[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_7.vb)]  
  
9. Następujące metody prywatnej odnaleźć pasującego nawiasu klamrowego na dowolnym poziomie zagnieżdżenia. Pierwsza metoda umożliwia znalezienie Zamknij znak, który pasuje do znaku Otwórz:  
  
     [!code-csharp[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_8.cs)]
     [!code-vb[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_8.vb)]  
  
10. Następująca metoda pomocnika umożliwia znalezienie Otwórz znak, który pasuje do znaku Zamknij:  
  
     [!code-csharp[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_9.cs)]
     [!code-vb[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_9.vb)]  
  
## <a name="implementing-a-brace-matching-tagger-provider"></a>Implementowanie parowanie nawiasów klamrowych dostawcy modułu znakowania  
 Oprócz wykonania modułu znakowania, musi także implementować i eksportowanie dostawcy modułu znakowania. W takim przypadku typ zawartości dostawcy jest "text". Oznacza to, że pasujących nawiasów klamrowych pojawi się w przypadku wszystkich typów plików tekstowych, ale implementacja pełniejsze powinna zostać zastosowana parowanie nawiasów klamrowych tylko do określonego typu zawartości.  
  
#### <a name="to-implement-a-brace-matching-tagger-provider"></a>Do implementowania dostawcy modułu znakowania pasującego nawiasu klamrowego  
  
1.  Zadeklaruj dostawcy modułu znakowania, która dziedziczy <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>, nadaj jej nazwę BraceMatchingTaggerProvider i wyeksportować go przy użyciu <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "tekst" i <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> z <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.  
  
     [!code-csharp[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_10.cs)]
     [!code-vb[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_10.vb)]  
  
2.  Implementowanie <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> metody tworzenia wystąpienia BraceMatchingTagger.  
  
     [!code-csharp[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_11.cs)]
     [!code-vb[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_11.vb)]  
  
## <a name="building-and-testing-the-code"></a>Tworzenie i testowanie kodu  
 Do przetestowania tego kodu, Skompiluj rozwiązanie BraceMatchingTest i uruchom go w eksperymentalnym wystąpieniu.  
  
#### <a name="to-build-and-test-bracematchingtest-solution"></a>Tworzenie i testowanie BraceMatchingTest rozwiązania  
  
1.  Skompiluj rozwiązanie.  
  
2.  Po uruchomieniu tego projektu w debugerze, drugie wystąpienie programu Visual Studio zostanie uruchomiony.  
  
3.  Utwórz plik tekstowy i wpisz tekst zawierający pasujących nawiasów klamrowych.  
  
    ```  
    hello {  
    goodbye}  
  
    {}  
  
    {hello}  
    ```  
  
4.  Po umieszczeniu karetkę przed otwierający nawias klamrowy zarówno tego nawias klamrowy, jak i zamknij pasującego nawiasu klamrowego powinien być zaznaczony. Po umieszczeniu kursora zaraz po Zamknij nawias klamrowy zarówno tego nawias klamrowy, jak i pasujące otwierający nawias klamrowy, powinien być zaznaczony.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: łączenie typu zawartości z rozszerzeniem nazwy pliku](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)