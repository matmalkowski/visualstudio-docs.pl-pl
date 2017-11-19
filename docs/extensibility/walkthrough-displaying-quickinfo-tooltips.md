---
title: "Wskazówki: Wyświetlanie podpowiedzi skrócone informacje | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - QuickInfo
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
caps.latest.revision: "27"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 303ce6608ee17b99995d871c5da1536a08fef335
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-displaying-quickinfo-tooltips"></a>Wskazówki: Wyświetlanie skrócone informacje etykietek narzędzi
Skrócone informacje to funkcja IntelliSense, która wyświetla podpisy metod i opisy, gdy użytkownik przesunie wskaźnik nad nazwę metody. Na podstawie języka funkcje, takie jak skrócone informacje można zaimplementować definiujący identyfikatory, dla których chcesz zawierają opisy skrócone informacje, a następnie utworzenie etykietka narzędzia, w którym ma być wyświetlana zawartość. Skrócone informacje można zdefiniować w kontekście usługi języka, można zdefiniować własny plik Nazwa rozszerzenia i zawartości typu i wyświetlić skrócone informacje dla właśnie tego typu lub skrócone informacje można wyświetlać dla istniejącego typu zawartości (na przykład "tekst"). Ten przewodnik przedstawia sposób wyświetlania skrócone informacje dla typu zawartości "text".  
  
 Przykład skrócone informacje w tym przewodniku Wyświetla etykietki narzędzi, gdy użytkownik przesunie wskaźnik nad nazwę metody. Ten projekt, musisz zaimplementować te interfejsy cztery:  
  
-   interfejs źródłowy  
  
-   interfejs dostawcy źródła  
  
-   Kontroler interfejsu  
  
-   interfejs dostawcy kontrolera  
  
 Dostawcy źródła i kontrolera są składnikami Managed Extensibility Framework (MEF) i są odpowiedzialne za eksportowanie klas źródła i kontrolera i importowanie usług i przekazuje informacje dotyczące takich jak <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>, co powoduje tekst etykietki narzędzia bufor i <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>, który wyzwala sesji skrócone informacje.  
  
 W tym przykładzie źródła skrócone informacje korzysta z listą ustalony metody nazwy i opisy, ale w pełnej implementacji usługi języka oraz dokumentację języka spoczywa odpowiedzialność za zapewnienie tej zawartości.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, użytkownik nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest uwzględniona jako opcjonalna funkcja w Instalatorze programu Visual Studio. Można także zainstalować zestawu SDK dla programu późniejsze. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Tworzenie projektu MEF  
  
#### <a name="to-create-a-mef-project"></a>Aby utworzyć projekt MEF  
  
1.  Tworzenie projektu C# VSIX. (W **nowy projekt** okno dialogowe, wybierz opcję **Visual C# / rozszerzalności**, następnie **projektu VSIX**.) Nazwa rozwiązania `QuickInfoTest`.  
  
2.  Dodaj szablon elementu klasyfikatora edytora do projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia z szablonem elementu edytor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Usuń pliki istniejące klasy.  
  
## <a name="implementing-the-quickinfo-source"></a>Implementowanie źródłowego skrócone informacje  
 Źródło QuickInfo jest odpowiedzialny za zbieranie zestaw identyfikatorów i ich opisy i dodawanie zawartości do buforu tekst etykietki narzędzia w przypadku jednego z identyfikatorów. W tym przykładzie identyfikatorów i ich opisy są dodawane tylko w Konstruktorze źródła.  
  
#### <a name="to-implement-the-quickinfo-source"></a>Aby zaimplementować źródła skrócone informacje  
  
1.  Dodaj plik klasy i nadaj mu nazwę `TestQuickInfoSource`.  
  
2.  Dodaj odwołanie do Microsoft.VisualStudio.Language.IntelliSense.  
  
3.  Dodaj następujące instrukcje importu.  
  
     [!code-vb[VSSDKQuickInfoTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_1.vb)]
     [!code-csharp[VSSDKQuickInfoTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_1.cs)]  
  
4.  Deklarowanie klasy, która implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>i nadaj mu nazwę `TestQuickInfoSource`.  
  
     [!code-vb[VSSDKQuickInfoTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_2.vb)]
     [!code-csharp[VSSDKQuickInfoTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_2.cs)]  
  
5.  Dodawanie pól dla dostawcy źródła skrócone informacje, buforu tekstu i zestaw nazwy metod i podpisy metod. W tym przykładzie nazwy metod i podpisy są inicjowane w `TestQuickInfoSource` konstruktora.  
  
     [!code-vb[VSSDKQuickInfoTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_3.vb)]
     [!code-csharp[VSSDKQuickInfoTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_3.cs)]  
  
6.  Dodaj konstruktora, który Ustawia dostawcę źródła skrócone informacje i buforu tekstu i wypełnia zestaw nazwy metod i podpisy metod i opisy.  
  
     [!code-vb[VSSDKQuickInfoTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_4.vb)]
     [!code-csharp[VSSDKQuickInfoTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_4.cs)]  
  
7.  Implementowanie <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A> metody. W tym przykładzie metoda znajduje bieżącego słowa lub poprzedniego wyrazu, jeśli kursor znajduje się na końcu wiersza lub bufor tekstowy. Jeśli słowo jest jednym z nazwy metody, opis dla tej nazwy metody jest dodawany do zawartości skrócone informacje.  
  
     [!code-vb[VSSDKQuickInfoTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_5.vb)]
     [!code-csharp[VSSDKQuickInfoTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_5.cs)]  
  
8.  Ponieważ również należy zaimplementować metodę Dispose() <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> implementuje <xref:System.IDisposable>:  
  
     [!code-vb[VSSDKQuickInfoTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_6.vb)]
     [!code-csharp[VSSDKQuickInfoTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_6.cs)]  
  
## <a name="implementing-a-quickinfo-source-provider"></a>Implementowanie dostawcy źródła skrócone informacje  
 Dostawca źródła skrócone informacje służy głównie w celu eksportowania się jako część MEF i utworzenia wystąpienia źródła skrócone informacje. Ponieważ to część MEF importowaniem innych części MEF.  
  
#### <a name="to-implement-a-quickinfo-source-provider"></a>Aby zaimplementować dostawcę źródła skrócone informacje  
  
1.  Zadeklarować dostawcę źródła skrócone informacje o nazwie `TestQuickInfoSourceProvider` implementującej <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>i wyeksportować go przy użyciu <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "Etykietka narzędzia skrócone informacje źródła" <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> z przed = "default", a <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "tekst".  
  
     [!code-vb[VSSDKQuickInfoTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_7.vb)]
     [!code-csharp[VSSDKQuickInfoTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_7.cs)]  
  
2.  Importowanie dwóch usług edytora, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> i <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>, jako właściwości `TestQuickInfoSourceProvider`.  
  
     [!code-vb[VSSDKQuickInfoTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_8.vb)]
     [!code-csharp[VSSDKQuickInfoTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_8.cs)]  
  
3.  Implementowanie <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A> do zwrócenia nowy `TestQuickInfoSource`.  
  
     [!code-vb[VSSDKQuickInfoTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_9.vb)]
     [!code-csharp[VSSDKQuickInfoTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_9.cs)]  
  
## <a name="implementing-a-quickinfo-controller"></a>Wdrażanie kontrolera skrócone informacje  
 Kontrolery skrócone informacje określają, kiedy skrócone informacje powinny być wyświetlane. W tym przykładzie QuickInfo jest wyświetlane, gdy wskaźnik znajduje się nad słowa, które odpowiada jednej nazwy metody. Kontroler QuickInfo implementuje obsługi zdarzenia przesuwania myszy wyzwalaną sesji skrócone informacje.  
  
#### <a name="to-implement-a-quickinfo-controller"></a>Aby zaimplementować kontrolera skrócone informacje  
  
1.  Deklarowanie klasy, która implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController>i nadaj mu nazwę `TestQuickInfoController`.  
  
     [!code-vb[VSSDKQuickInfoTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_10.vb)]
     [!code-csharp[VSSDKQuickInfoTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_10.cs)]  
  
2.  Dodaj pola prywatne dla widoku tekstu buforów tekst reprezentowane w widoku tekstu, sesji skrócone informacje oraz skrócone informacje dostawcy kontrolera.  
  
     [!code-vb[VSSDKQuickInfoTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_11.vb)]
     [!code-csharp[VSSDKQuickInfoTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_11.cs)]  
  
3.  Dodaj Konstruktor, który ustawia pola i dodanie obsługi zdarzeń przesuwania myszy.  
  
     [!code-vb[VSSDKQuickInfoTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_12.vb)]
     [!code-csharp[VSSDKQuickInfoTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_12.cs)]  
  
4.  Dodawanie obsługi zdarzeń przesuwania myszy, który wyzwala sesji skrócone informacje.  
  
     [!code-vb[VSSDKQuickInfoTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_13.vb)]
     [!code-csharp[VSSDKQuickInfoTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_13.cs)]  
  
5.  Implementowanie <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A> metodę, tak że usuwa obsługi zdarzeń przesuwania myszy odłączeniem kontrolera z widoku tekstu.  
  
     [!code-vb[VSSDKQuickInfoTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_14.vb)]
     [!code-csharp[VSSDKQuickInfoTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_14.cs)]  
  
6.  Implementowanie <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A> — metoda i <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> metodę jako puste metody w tym przykładzie.  
  
     [!code-vb[VSSDKQuickInfoTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_15.vb)]
     [!code-csharp[VSSDKQuickInfoTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_15.cs)]  
  
## <a name="implementing-the-quickinfo-controller-provider"></a>Implementowanie dostawcy kontrolera skrócone informacje  
 Dostawca kontrolera skrócone informacje służy głównie w celu eksportowania się jako część MEF i utworzenia wystąpienia kontrolera skrócone informacje. Ponieważ to część MEF importowaniem innych części MEF.  
  
#### <a name="to-implement-the-quickinfo-controller-provider"></a>Do implementowania dostawcy kontrolera skrócone informacje  
  
1.  Deklarowanie klasy o nazwie `TestQuickInfoControllerProvider` implementującej <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider>i wyeksportować go przy użyciu <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "Etykietka narzędzia kontrolera skrócone informacje" i <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "tekst":  
  
     [!code-vb[VSSDKQuickInfoTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_16.vb)]
     [!code-csharp[VSSDKQuickInfoTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_16.cs)]  
  
2.  Importuj <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> jako właściwość.  
  
     [!code-vb[VSSDKQuickInfoTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_17.vb)]
     [!code-csharp[VSSDKQuickInfoTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_17.cs)]  
  
3.  Implementowanie <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A> metody tworzenia wystąpienia kontrolera skrócone informacje.  
  
     [!code-vb[VSSDKQuickInfoTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_18.vb)]
     [!code-csharp[VSSDKQuickInfoTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_18.cs)]  
  
## <a name="building-and-testing-the-code"></a>Tworzenie i testowanie kodu  
 Do przetestowania tego kodu, Skompiluj rozwiązanie QuickInfoTest i uruchom go w eksperymentalnym wystąpieniu.  
  
#### <a name="to-build-and-test-the-quickinfotest-solution"></a>Tworzenie i testowanie rozwiązania QuickInfoTest  
  
1.  Skompiluj rozwiązanie.  
  
2.  Po uruchomieniu tego projektu w debugerze, drugie wystąpienie programu Visual Studio zostanie uruchomiony.  
  
3.  Utwórz plik tekstowy i wpisz tekst, który zawiera wyrazy "Dodaj" i "subtract".  
  
4.  Przesuń wskaźnik myszy na jednym z wystąpień "Dodaj". Podpis i opis `add` metoda powinna być wyświetlana.  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Łączenie typu zawartości z rozszerzeniem nazwy pliku](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)