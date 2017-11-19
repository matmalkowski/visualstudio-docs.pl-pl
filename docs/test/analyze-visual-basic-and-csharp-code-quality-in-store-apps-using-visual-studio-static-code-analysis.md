---
title: "Analiza jakości kodu Visual Basic i C# w aplikacji platformy uniwersalnej systemu Windows przy użyciu programu Visual Studio statycznej analizy kodu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.propertypages.csvb.express
ms.assetid: cab553fc-19a9-4cbf-858e-8200258ffe50
caps.latest.revision: "14"
author: erickson-doug
ms.author: douge
manager: douge
ms.openlocfilehash: e61f307872f60da316480d3654507b5225588f41
ms.sourcegitcommit: c0422a3d594ea5ae8fc03f1aee684b04f417522e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2017
---
# <a name="analyze-visual-basic-and-c-code-quality-in-uwp-apps-using-visual-studio-static-code-analysis"></a>Analiza jakości kodu Visual Basic i C# w aplikacji platformy uniwersalnej systemu Windows przy użyciu programu Visual Studio statycznej analizy kodu
![Ma zastosowanie do systemu Windows i Windows Phone](../debugger/media/windows_and_phone_content.png "windows_and_phone_content")  
  
 Narzędzie do analizy kodu w programie Visual Studio Express sprawdza, czy kod zestaw typowych wady i naruszeń dobrych praktyk programowania. Ostrzeżenia analizy kodu różnią się od błędów i ostrzeżeń, ponieważ narzędzie do analizy kodu wyszukuje wzorce określonego kodu, które są prawidłowe, ale nadal można utworzyć problemy lub innym osobom korzystającym z kodu. Kod — analiza znajduje się też wady w kodzie, które są trudne do odnajdywania testy. Uruchomione narzędzie do analizy kodu w regularnych odstępach czasu w procesie tworzenia aplikacji może zwiększyć jakość aplikacji ukończone.  
  
> [!NOTE]
>  W Visual Studio Ultimate, Visual Studio Premium i Visual Studio Professional można użyć pełną funkcjonalność analizy kodu. Zobacz [analiza jakości aplikacji za pomocą narzędzi analizy kodu](http://msdn.microsoft.com/library/dd264897.aspx) w bibliotece MSDN.  
  
## <a name="in-this-topic"></a>W tym temacie:  
 Informacje na temat:  
  
 [Przeprowadzanie analizy kodu](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Run)  
  
 [Analizowanie i rozwiązywanie ostrzeżenia analizy kodu](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Analyze)  
  
 [Pomijanie ostrzeżeń analizy kodu](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Suppress)  
  
 [Wyszukiwanie i filtrowanie wyników analizy kodu](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Search)  
  
 [Ostrzeżeń analizy kodu w języku Visual Basic i C#](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Warnings)  
  
##  <a name="BKMK_Run"></a>Przeprowadzanie analizy kodu  
 Aby uruchamiać analizy kodu w rozwiązaniu programu Visual Studio:  
  
-   Na **kompilacji** menu, wybierz **uruchamiania analizy kodu dla rozwiązania**.  
  
 Do automatycznego uruchamiania analizy kodu za każdym razem, w przypadku kompilowania projektu:  
  
1.  Kliknij prawym przyciskiem myszy nazwę projektu w Eksploratorze rozwiązań, a następnie wybierz pozycję **właściwości**.  
  
2.  Na stronie właściwości projektu, wybierz **analizy kodu** , a następnie wybierz **Włącz analizę kodu podczas kompilacji (definiuje stała analizy kodu)**.  
  
 Rozwiązanie jest skompilowany i uruchamia analizy kodu. Wyniki są wyświetlane w oknie analizy kodu.  
  
 ![W oknie analizy kodu](../test/media/ca_managed_collapsed.png "CA_Managed_Collapsed")  
  
##  <a name="BKMK_Analyze"></a>Analizowanie i rozwiązywanie ostrzeżenia analizy kodu  
 Do analizowania określone ostrzeżenia, należy kliknąć tytuł ostrzeżenie w oknie analizy kodu. Ostrzeżenie rozszerza się, aby wyświetlić szczegółowe informacje o problemie.  
  
 ![Rozszerzony kod analizy ostrzeżenia](../test/media/ca_managed_callouts.png "CA_Managed_Callouts")  
  
 Po rozwinięciu ostrzeżenie wiersza kodu, która spowodowała ostrzeżenie zostanie wyróżniona w edytorze kodu programu Visual Studio.  
  
 ![Kod wyróżnianie tekstu analizy](../test/media/ca_managed_sourceline.png "CA_Managed_SourceLine")  
  
 Po zidentyfikowaniu problem można rozwiązać, w kodzie. Następnie uruchom ponownie analizę kodu, aby upewnić się, że ostrzeżenia nie jest już widoczna w oknie analizy kodu i nie ma Twojego poprawka nie zgłaszany nowego ostrzeżenia.  
  
> [!TIP]
>  Można ponownie uruchomić analizy kodu w oknie analizy kodu. Kliknij przycisk **Analizuj** przycisk i wybierz zakres analizy. Można ponownie uruchomić analizy całego rozwiązania lub wybranego projektu.  
  
##  <a name="BKMK_Suppress"></a>Pomijanie ostrzeżeń analizy kodu  
 Brak razy podczas może zdecydować, czy nie, aby naprawić ostrzeżenia analizy kodu. Możesz określić rozpoznawanie ostrzeżenia wymaga zbyt dużo nagrywanie względem prawdopodobieństwo, że ten problem może wystąpić w implementacji rzeczywistych kodu. Lub może uważasz, że analizy, który jest używany w ostrzeżenia jest nieodpowiedni dla określonego kontekstu. Ostrzeżeń indywidualnych można pominąć, tak aby nie były widoczne w oknie analizy kodu.  
  
 Aby wyłączyć ostrzeżenia:  
  
1.  Jeśli nie są wyświetlane szczegółowe informacje, należy kliknąć tytuł ostrzeżenia, aby go rozwinąć.  
  
2.  Wybierz **akcje** łącze umieszczone u dołu ostrzeżenia.  
  
3.  Wskaż **Pomiń komunikat** i wybrać opcję **źródła w** lub **w pliku pominięć**.  
  
    -   **W źródle** wstawia `SuppressMessage` atrybutu w pliku źródłowym powyżej metody, który wygenerował ostrzeżenia. Dzięki temu pomijanie mogą szybciej odnajdywać.  
  
    -   **W pliku pominięć** dodaje `SuppressMessage` atrybutu **GlobalSuppressions.cs** pliku projektu. To może ułatwić zarządzanie pominięć. Należy pamiętać, że `SuppressMessage` dodany atrybut **GlobalSuppression.cs** dotyczy również metody, który wygenerował ostrzeżenia. Pomijaj ostrzeżenia globalnie.  
  
     Decyzji, czy pominąć to ostrzeżenie w pliku źródłowym lub w pliku pominięć zależy od styl kodowania i potrzeb.  
  
##  <a name="BKMK_Search"></a>Wyszukiwanie i filtrowanie wyników analizy kodu  
 Możesz przeszukać długich list komunikaty ostrzegawcze i można filtrować ostrzeżeń w rozwiązań dotyczących wielu projektów.  
  
 ![Wyszukiwanie i filtrowanie oknie analizy kodu](../test/media/ca_searchfilter.png "CA_SearchFilter")  
  
 W [!INCLUDE[vs_dev11_expwin_long](../misc/includes/vs_dev11_expwin_long_md.md)], wszystkie kod analizy ostrzeżenia ma poziom ważności ostrzeżenie.  
  
##  <a name="BKMK_Warnings"></a>Ostrzeżeń analizy kodu w języku Visual Basic i C#  
 Kod — analiza zgłasza następujące ostrzeżenia:  
  
 [CA1001: Typy, które posiadają pola usuwalne powinny być usuwalne](http://msdn.microsoft.com/library/ms182172.aspx)  
  
 [CA1821: Usuń puste finalizatory](http://msdn.microsoft.com/library/bb264476.aspx)  
  
 [CA2213: Pola usuwalne powinny zostać usunięte](http://msdn.microsoft.com/library/ms182328.aspx)  
  
 [CA2229: Zaimplementować konstruktory serializacji](http://msdn.microsoft.com/library/ms182343.aspx)  
  
 [CA2231: Przeciąż operator equals przy zastępowaniu ValueType.Equals](http://msdn.microsoft.com/library/ms182359.aspx)
