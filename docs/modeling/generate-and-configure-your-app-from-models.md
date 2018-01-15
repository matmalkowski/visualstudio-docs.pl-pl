---
title: Generowanie i konfigurowanie aplikacji na podstawie modeli | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 15d6d64a094923e3f7f1f4bb5778404ffcc1587e
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2018
---
# <a name="generate-and-configure-your-app-from-models"></a>Generowanie i konfigurowanie aplikacji na podstawie modeli
Można wygenerować lub skonfigurować części aplikacji z modelu.
  
 Model reprezentuje wymagania bezpośrednio od kodu. Przez wyprowadzanie zachowania aplikacji bezpośrednio z modelu, mogą odpowiadać na zmianę wymagań znacznie więcej szybkie i niezawodne niż aktualizowanie kodu. Mimo że niektóre początkowej pracy jest wymagane do skonfigurowania wyprowadzenia, inwestycji jest zwracany, Jeśli przypuszczasz, zmiany w wymaganiach lub jeśli planujesz wykonanie kilku różnych wariantów produktu.  
  
## <a name="generating-the-code-of-your-application-from-a-model"></a>Generowanie kodu aplikacji na podstawie modelu  
 Najprostszym sposobem, aby wygenerować kod jest przy użyciu szablonów tekstowych. Istnieje możliwość wygenerowania kodu, w tym samym [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozwiązania, w którym można przechowywać modelu. Aby uzyskać więcej informacji, zobacz:  
  
-   [Generowanie kodu czasu projektowania przy użyciu szablonów tekstowych T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)  
  
-   [Generowanie kodu z języka specyficznego dla domeny](../modeling/generating-code-from-a-domain-specific-language.md)  
  
 Ta metoda jest stosowany przyrostowo. Uruchom z aplikacją, która działa tylko dla określonych przypadków, a następnie wybierz kilka części o tym, który ma zostać różnią się w modelu. Zmień nazwę plików źródłowych z tych elementów, dzięki czemu staną się plikami tekstowymi szablonu (.TT —). W tym momencie pliki źródłowe .cs będą automatycznie generowane z plików szablonu, aplikacja będzie działać tak jak poprzednio.  
  
 Następnie możesz wykonać jedną z części kodu i Zamień tekst wyrażenia szablonu, który odczytuje modelu i generuje część pliku źródłowego. Co najmniej jedną wartość modelu powinna generować oryginalne źródło, aby ponownie uruchomić aplikację i będzie działać jak poprzednio. Po przetestowaniu wartości inny model, możesz przejść do wstawienia szablonowe w innej części kodu.  
  
 Ta metoda przyrostowe oznacza, że generowanie kodu jest zazwyczaj podejście niskiego ryzyka. Wynikowa aplikacji zwykle wykonać prawie oraz odręcznego wersji.  
  
 Jednak po uruchomieniu z istniejącej aplikacji, może się okazać, że wiele refaktoryzacji jest wymagana do oddzielania różne zachowania, które są objęte modelu, dzięki czemu może być niezależnie zmieniać. Firma Microsoft zaleca ocenić ten aspekt aplikacji, podczas szacowania kosztów projektu.  
  
## <a name="configuring-your-application-from-a-model"></a>Konfigurowanie aplikacji z modelu  
 Do zmiany zachowania aplikacji w czasie wykonywania, nie można użyć generowania kodu, który generuje kod źródłowy, aby aplikacja została skompilowana. Zamiast tego można zaprojektować aplikacji ma zostać odczytany model i odpowiednio różnicującej jego zachowania. Aby uzyskać więcej informacji, zobacz:  
  
-   [Instrukcje: Otwieranie modelu z pliku w kodzie programu](../modeling/how-to-open-a-model-from-file-in-program-code.md)  
  
 Ta metoda również będą stosowane przyrostowo, ale więcej pracy na początku. Należy napisać kod, który zostanie odczytany model i skonfiguruj struktury, która umożliwia jego wartości umożliwić dostęp do zmiennej części. Tworzenie ogólnych części zmiennej jest droższe niż generowanie kodu.  
  
 Aplikacja ogólna zazwyczaj wykonuje także mniej niż jego odpowiedników określone. Jeśli wydajność jest niezwykle ważny, planu projektu powinien zawierać ocenę to zagrożenie.  
  
## <a name="developing-a-derived-application"></a>Opracowanie aplikacji pochodne  
 Może być przydatne następujące ogólne wytyczne.  
  
-   **Uruchom określone, a następnie Uogólnij.** Najpierw zapisać określonej wersji aplikacji. Ta wersja powinny działać w jednym zestawie warunków. Po zakończeniu jego działa poprawnie, możesz wprowadzić niektóre on pochodzić z modelu. Rozszerzanie stopniowo pochodnej części.  
  
     Na przykład projekt witryny sieci Web, który ma określony zestaw stron sieci Web przed rozpoczęciem projektowania aplikacji sieci Web prezentuje stron, które są zdefiniowane w modelu.  
  
-   **Model aspekty typu variant.** Zidentyfikuj aspektów, które będą się różnić między wdrożenia jednego i drugiego, lub w czasie, gdy wymagania dotyczące zmiany. Są to aspektów, które powinny pochodzić z modelu.  
  
     Na przykład jeśli zestaw sieci Web pages i łącza między ich zmiany, ale styl i format stron jest zawsze taki sam, a następnie modelu powinna zawierać opis łącza, ale nie ma do opisywania formatu strony.  
  
-   **Oddzielne problemy.** Jeśli aspekty zmiennej można podzielić na niezależne obszarów, użycia osobnych modeli dla każdego obszaru. ModelBus można zdefiniować operacje, które mają wpływ zarówno modeli i ograniczenia między nimi.  
  
     Na przykład użyć jednego modelu do zdefiniowania nawigacji między stronami sieci Web i inny model, do definiowania układu strony.
  
-   **Model to wymaganie nie rozwiązania.** Projektowanie modelu, tak aby wymagania użytkownika. Z kolei nie zaprojektować notacji zgodnie ze zmiennej aspektów wdrożenia.  
  
     Na przykład model nawigacji sieci Web powinno reprezentować stron sieci Web i hiperłącza między nimi. Model nawigacji sieci Web nie powinno reprezentować fragmentów kodu HTML lub klas w aplikacji.  
  
-   **Generowanie i interpretowania?** Jeśli wymagania dotyczące konkretnego wdrożenia rzadko ulegnie zmianie, generowanie kodu programu na podstawie modelu. Wymagania często mogą ulec zmianie lub mogą współistnieć w więcej niż jeden typ variant w tym samym wdrożeniu, zapisu aplikacji, dzięki czemu może odczytywać i interpretować modelu.  
  
     Na przykład jeśli używasz modelu witryny sieci Web umożliwiające tworzenie szereg różnych i oddzielnie zainstalowanego witryn sieci Web, następnie należy generować kod lokacji z modelu. Jednak go użyć modelu do sterowania lokacji, który zmienia codziennie, wówczas jest napisanie serwer sieci Web odczytuje modelu i w związku z tym przedstawia informacje o lokacji.  
  
-   **UML lub DSL?** Należy rozważyć utworzenie ustawienia notacji modelowania przy użyciu stereotypy w celu rozszerzenia kodu UML. Zdefiniuj DSL, jeśli nie diagram UML, która pasuje do tego celu. Jednak uniknąć dzielenia standardowa semantyka UML.  
  
     Na przykład diagram klasy UML jest kolekcją pola i strzałki; w tym notacji teoretycznie zdefiniować żadnych czynności. Jednak nie zaleca się używanie diagramu klas, z wyjątkiem przypadków, gdy są w rzeczywistości opisujące zestaw typów. Na przykład można dostosować diagramy klas opisujących różne rodzaje stron sieci Web.  
  
## <a name="see-also"></a>Zobacz też  
 [Generowanie kodu z języka specyficznego dla domeny](../modeling/generating-code-from-a-domain-specific-language.md)   
 [Porady: Otwieranie modelu z pliku w kodzie programu](../modeling/how-to-open-a-model-from-file-in-program-code.md)   
 [Generowanie kodu czasu projektowania przy użyciu szablonów tekstowych T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)