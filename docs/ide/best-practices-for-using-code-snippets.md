---
title: "Najlepsze rozwiązania dotyczące korzystania z wstawek kodu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code snippets, best practices
- code snippets, security
ms.assetid: a293ec17-4dd7-4a99-8eeb-99f44a822a8b
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 34424ae13a47008eaefa3634f2bf25d31daf285e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="best-practices-for-using-code-snippets"></a>Najlepsze praktyki dotyczące korzystania z wstawek kodu
Kod w fragment kodu przedstawia tylko najbardziej podstawową metodą coś zrobić. Dla większości aplikacji należy zmodyfikować kod do własnych aplikacji.  
  
## <a name="handling-exceptions"></a>Obsługa wyjątków  
 Zazwyczaj fragment kodu Try... Bloki catch przechwytuje i rethrow wszystkie wyjątki. Może to nie być odpowiednie opcje dla projektu. Dla każdego wyjątku Brak odpowiedzi na kilka sposobów. Przykłady można znaleźć [porady: obsługa wyjątków za pomocą bloku try/catch (C# przewodnik programowania w języku)](/dotnet/csharp/programming-guide/exceptions/how-to-handle-an-exception-using-try-catch) i [spróbuj... CATCH... Instrukcji finally](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement).  
  
## <a name="file-locations"></a>Lokalizacje plików  
 Podczas lokalizacji plików dostosowania się do aplikacji, możesz pomyśleć o następujących czynności:  
  
-   Znajdowanie dostępnej lokalizacji. Użytkownicy mogą nie mieć dostępu do folderu Program Files na komputerze, dlatego przechowywanie plików z plikami aplikacji może nie działać.  
  
-   Znajdowanie w bezpiecznej lokalizacji. Przechowywanie plików w folderze głównym (C:\\) nie jest bezpieczna. Dla danych aplikacji firma Microsoft zaleca \Application folderu danych. Dla danych poszczególnych użytkowników aplikacji można utworzyć pliku dla każdego użytkownika w folderze dokumenty \My.  
  
-   Przy użyciu prawidłową nazwę pliku. Można użyć <xref:System.Windows.Forms.OpenFileDialog> i <xref:System.Windows.Forms.SaveFileDialog> formantów, aby zmniejszyć prawdopodobieństwo nieprawidłowych nazw plików. Należy pamiętać, że między czasem użytkownik wybierze plik i czas kodu manipuluje pliku, plik może być usunięty. Ponadto użytkownik może nie ma uprawnień do zapisu w pliku.  
  
## <a name="security"></a>Zabezpieczenia  
 Jak bezpieczne fragment jest zależy od tego, gdzie jest używane w kodzie źródłowym oraz jak zmienić po w kodzie. Poniższa lista zawiera kilka obszarów, które należy wziąć pod uwagę.  
  
-   Dostępu do plików i bazy danych  
  
-   Zabezpieczenia dostępu kodu  
  
-   Ochrona zasobów (takich jak dzienniki zdarzeń, rejestr)  
  
-   Przechowywanie kluczy tajnych  
  
-   Weryfikowanie, czy dane wejściowe  
  
-   Przekazywanie danych do technologii skryptów  
  
 Aby uzyskać więcej informacji, zobacz [zabezpieczania aplikacji](../ide/securing-applications.md).  
  
## <a name="downloaded-code-snippets"></a>Wstawki kodu pobrany  
 Wstawki kodu IntelliSense zainstalowany przez program Visual Studio nie są w sobie zagrożenie bezpieczeństwa. Mogą jednak utworzyć zagrożenia bezpieczeństwa w aplikacji. Wstawki kodu programu pobrane z Internetu powinny być traktowane jak inne pobieranej zawartości — z najwyższą ostrożność.  
  
-   Pobierz wstawki tylko z witryn, którym ufasz, a wirusów aktualne oprogramowanie.  
  
-   Otwórz wszystkie pliki pobrane fragmentu kodu w Notatniku lub edytora XML programu Visual Studio i uważnie przeczytać przed zainstalowaniem ich. Poszukaj następujących problemów:  
  
    -   Jeśli zostanie wykonana, fragment kodu może uszkodzić system. Należy uważnie przeczytać kod źródłowy przed jego uruchomieniem.  
  
    -   Blok adresu URL pomocy fragment pliku może zawierać adresów URL, które wykonać pliku skryptu złośliwego lub wyświetlić obraźliwe witryny sieci Web.  
  
    -   Fragment kodu może zawierać odwołań, które są dodawane w trybie dyskretnym do projektu i mogą być ładowane z dowolnego miejsca w systemie. Te odwołania mogą została pobrana do komputera, z którego został pobrany fragment kodu. Fragment kodu może następnie wprowadzić wywołanie do metody w odwołaniu, która wykonuje złośliwego kodu. Aby zabezpieczyć się przed takimi atakami, przejrzyj bloki importów i odwołania do pliku fragmentu.  
  
## <a name="see-also"></a>Zobacz też  
 [Wstawki kodu IntelliSense języka Visual Basic](/dotnet/visual-basic/developing-apps/using-ide/intellisense-code-snippets)   
 [Zabezpieczanie aplikacji](../ide/securing-applications.md)   
 [Wstawki kodu](../ide/code-snippets.md)