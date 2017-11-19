---
title: "Wskazówki: Tworzenie konspektu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
caps.latest.revision: "30"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f503d9e8b0ef125fdb72ea60a9928f308b900993
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-outlining"></a>Wskazówki: Tworzenie konspektu
Można zaimplementować opartych na języku funkcje, takie jak tworzenie konspektu, definiując rodzaje regionów tekst, który chcesz rozwiń lub Zwiń. Regiony można zdefiniować w kontekście usługi języka, można zdefiniować własny plik Nazwa rozszerzenia i zawartości typu i dotyczą definicji region tylko tego typu lub definicje regionie można zastosować do istniejącego typu zawartości (na przykład "tekst"). W tym przewodniku pokazano, jak zdefiniować i wyświetlanie konspektu regionów.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, użytkownik nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest uwzględniona jako opcjonalna funkcja w Instalatorze programu Visual Studio. Można także zainstalować zestawu SDK dla programu późniejsze. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Tworzenie projektu Framework (MEF) zarządzanych rozszerzeń  
  
#### <a name="to-create-a-mef-project"></a>Aby utworzyć projekt MEF  
  
1.  Tworzenie projektu VSIX. Nazwa rozwiązania `OutlineRegionTest`.  
  
2.  Dodaj szablon elementu klasyfikatora edytora do projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia z szablonem elementu edytor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Usuń pliki istniejące klasy.  
  
## <a name="implementing-an-outlining-tagger"></a>Implementowanie zwijania modułu znakowania  
 Regiony zwijania są oznaczane rodzaj tagu (<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>). Ten tag zawiera standardowe zwijania zachowanie. Region obramowane można rozwinięte lub zwinięte. Obramowane region jest oznaczony jako znak PLUS, jeśli jest zwinięte lub znakiem minus, jeśli rozwiniętą i rozszerzonej region został oddzielony przez pionowym wierszem.  
  
 W poniższej procedurze pokazano sposób definiowania modułu znakowania, tworzącą zwijania regiony dla wszystkich regionów, które są rozdzielane znakami "[" i "]".  
  
#### <a name="to-implement-an-outlining-tagger"></a>Aby zaimplementować zwijania modułu znakowania  
  
1.  Dodaj plik klasy i nadaj mu nazwę `OutliningTagger`.  
  
2.  Importuj następujących przestrzeni nazw.  
  
     [!code-csharp[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/CSharp/walkthrough-outlining_1.cs)]
     [!code-vb[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_1.vb)]  
  
3.  Utwórz klasę o nazwie `OutliningTagger`, a go zaimplementować <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>:  
  
     [!code-csharp[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/CSharp/walkthrough-outlining_2.cs)]
     [!code-vb[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_2.vb)]  
  
4.  Dodaj pola do śledzenia buforu tekstu i migawki i gromadzone zestawów wierszy, które powinny oznakowane jako zwijania regionów. Ten kod zawiera listę obiektów Region (w celu zdefiniowania później) reprezentujące zwijania regionów.  
  
     [!code-csharp[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/CSharp/walkthrough-outlining_3.cs)]
     [!code-vb[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_3.vb)]  
  
5.  Dodaj Konstruktor modułu znakowania, które inicjuje pola, analizuje buforu i dodaje obsługi zdarzeń do <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> zdarzeń.  
  
     [!code-csharp[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/CSharp/walkthrough-outlining_4.cs)]
     [!code-vb[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_4.vb)]  
  
6.  Implementowanie <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> obejmuje metodę, która tworzy wystąpienie tagu. W tym przykładzie założono, że zakresy w <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> przekazany do metody są ciągłe, mimo że to nie zawsze jest wielkość liter. Ta metoda tworzy nowy zakres tagu dla każdego z możliwością zwijania regionów.  
  
     [!code-csharp[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/CSharp/walkthrough-outlining_5.cs)]
     [!code-vb[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_5.vb)]  
  
7.  Deklarowanie `TagsChanged` obsługi zdarzeń.  
  
     [!code-csharp[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/CSharp/walkthrough-outlining_6.cs)]
     [!code-vb[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_6.vb)]  
  
8.  Dodaj `BufferChanged` obsługi zdarzeń, które odpowiada <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> zdarzenia według podczas analizowania buforu tekstu.  
  
     [!code-csharp[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/CSharp/walkthrough-outlining_7.cs)]
     [!code-vb[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_7.vb)]  
  
9. Dodaj metodę analizowania buforu. Przykładzie podanym w tym miejscu jest tylko do celów ilustracyjnych. Analizuje synchronicznie buforu w zagnieżdżonych zwijania regionów.  
  
     [!code-csharp[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/CSharp/walkthrough-outlining_8.cs)]
     [!code-vb[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_8.vb)]  
  
10. Następująca metoda pomocnika pobiera liczba całkowita, która reprezentuje poziom zwijania, tak, aby 1 pary nawiasów klamrowych po lewej stronie.  
  
     [!code-csharp[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/CSharp/walkthrough-outlining_9.cs)]
     [!code-vb[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_9.vb)]  
  
11. Następująca metoda pomocnika tłumaczy Region (zdefiniowaną w dalszej części tego tematu) na element SnapshotSpan.  
  
     [!code-csharp[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/CSharp/walkthrough-outlining_10.cs)]
     [!code-vb[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_10.vb)]  
  
12. Następujący kod jest tylko do celów ilustracyjnych. Definiuje klasę PartialRegion, zawierającą numer wiersza i Przesunięcie początku zwijania regionu i odwołanie do regionu nadrzędnego (jeśli istnieje). Dzięki temu analizatora składni skonfigurować zagnieżdżone zwijania regionów. Klasa pochodna Region zawiera odwołanie do numeru wiersza końcowego zwijania regionu.  
  
     [!code-csharp[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/CSharp/walkthrough-outlining_11.cs)]
     [!code-vb[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_11.vb)]  
  
## <a name="implementing-a-tagger-provider"></a>Implementowanie dostawcy modułu znakowania  
 Należy wyeksportować dostawcy modułu znakowania dla Twojego modułu znakowania. Tworzy dostawcę modułu znakowania `OutliningTagger` buforu typ zawartości "text" lub innego zwraca `OutliningTagger` Jeśli bufor już ją zawiera.  
  
#### <a name="to-implement-a-tagger-provider"></a>Aby zaimplementować dostawcę modułu znakowania  
  
1.  Utwórz klasę o nazwie `OutliningTaggerProvider` implementującej <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>i wyeksportować go przy użyciu atrybutów ContentType i typu tag.  
  
     [!code-csharp[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/CSharp/walkthrough-outlining_12.cs)]
     [!code-vb[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_12.vb)]  
  
2.  Implementowanie <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> metody przez dodanie `OutliningTagger` właściwości buforu.  
  
     [!code-csharp[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/CSharp/walkthrough-outlining_13.cs)]
     [!code-vb[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_13.vb)]  
  
## <a name="building-and-testing-the-code"></a>Tworzenie i testowanie kodu  
 Do przetestowania tego kodu, Skompiluj rozwiązanie OutlineRegionTest i uruchom go w eksperymentalnym wystąpieniu.  
  
#### <a name="to-build-and-test-the-outlineregiontest-solution"></a>Tworzenie i testowanie rozwiązania OutlineRegionTest  
  
1.  Skompiluj rozwiązanie.  
  
2.  Po uruchomieniu tego projektu w debugerze, drugie wystąpienie programu Visual Studio zostanie uruchomiony.  
  
3.  Utwórz plik tekstowy. Wpisz dowolny tekst, który obejmuje zarówno otwierający nawias klamrowy, jak i zamykający nawias klamrowy.  
  
    ```  
    [  
       Hello  
    ]  
    ```  
  
4.  Powinien być zwijania region, który zawiera zarówno nawiasów klamrowych. Należy kliknąć znak MINUS z lewej strony otwierający nawias klamrowy, aby zwinąć zwijania regionu. Gdy region jest zwinięte, symbol wielokropka (...) powinna zostać wyświetlona z lewej strony obszaru zwiniętego i wyskakujące okienko zawierające tekst **Aktywuj tekst** powinien zostać wyświetlony, gdy wskaźnik myszy znajduje się nad wielokropka.  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Łączenie typu zawartości z rozszerzeniem nazwy pliku](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)