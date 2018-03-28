---
title: Najlepsze rozwiązania dotyczące korzystania z wstawek kodu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code snippets, best practices
- code snippets, security
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 6d5ac19f3caa795fc309b77d0845db0d412e1ccb
ms.sourcegitcommit: 29ef88fc7d1511f05e32e9c6e7433e184514330d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2018
---
# <a name="best-practices-for-using-code-snippets"></a>Najlepsze rozwiązania dotyczące korzystania z wstawek kodu

Kod w fragment kodu przedstawia tylko najbardziej podstawową metodą coś zrobić. Dla większości aplikacji należy zmodyfikować kod do własnych aplikacji.

## <a name="handling-exceptions"></a>Obsługa wyjątków

Zazwyczaj fragment kodu Try... Bloki catch przechwytuje i rethrow wszystkie wyjątki. Może to nie być odpowiednie opcje dla projektu. Dla każdego wyjątku Brak odpowiedzi na kilka sposobów. Przykłady można znaleźć [porady: obsługa wyjątków za pomocą bloku try/catch (C#)](/dotnet/csharp/programming-guide/exceptions/how-to-handle-an-exception-using-try-catch) i [spróbuj... CATCH... Finally — instrukcja (Visual Basic)](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement).

## <a name="file-locations"></a>Lokalizacje plików

Podczas lokalizacji plików dostosowania się do aplikacji, możesz pomyśleć o następujących czynności:

- Znajdowanie dostępnej lokalizacji. Użytkownicy mogą nie mieć dostępu do *Program Files* folderu na komputerze, dlatego przechowywanie plików z aplikacją plików może nie służbowych.

- Znajdowanie w bezpiecznej lokalizacji. Przechowywanie plików w folderze głównym (*C:\\*) nie jest bezpieczna. Dla danych aplikacji, firma Microsoft zaleca *danych aplikacji* folderu. Dla danych poszczególnych użytkowników aplikacji można utworzyć pliku dla każdego użytkownika w *dokumenty* folderu.

- Przy użyciu prawidłową nazwę pliku. Można użyć <xref:System.Windows.Forms.OpenFileDialog> i <xref:System.Windows.Forms.SaveFileDialog> formantów, aby zmniejszyć prawdopodobieństwo nieprawidłowych nazw plików. Należy pamiętać, że między czasem użytkownik wybierze plik i czas kodu manipuluje pliku, plik może być usunięty. Ponadto użytkownik może nie ma uprawnień do zapisu w pliku.

## <a name="security"></a>Zabezpieczenia

Jak bezpieczne fragment jest zależy od tego, gdzie jest używane w kodzie źródłowym oraz jak zmienić po w kodzie. Poniższa lista zawiera kilka obszarów, które należy wziąć pod uwagę.

- Dostępu do plików i bazy danych

- Zabezpieczenia dostępu kodu

- Ochrona zasobów (takich jak dzienniki zdarzeń, rejestr)

- Przechowywanie kluczy tajnych

- Weryfikowanie, czy dane wejściowe

- Przekazywanie danych do technologii skryptów

Aby uzyskać więcej informacji, zobacz [zabezpieczanie aplikacji](../ide/securing-applications.md).

## <a name="downloaded-code-snippets"></a>Wstawki kodu pobrany

Wstawki kodu IntelliSense zainstalowany przez program Visual Studio nie są w sobie zagrożenie bezpieczeństwa. Mogą jednak utworzyć zagrożenia bezpieczeństwa w aplikacji. Wstawki kodu programu pobrane z Internetu powinny być traktowane jak inne pobieranej zawartości — z najwyższą ostrożność.

- Pobierz wstawki tylko z witryn, którym ufasz, a wirusów aktualne oprogramowanie.

- Otwórz wszystkie pliki pobrane fragmentu kodu w Notatniku lub edytora XML programu Visual Studio i uważnie przeczytać przed zainstalowaniem ich. Poszukaj następujących problemów:

    - Jeśli zostanie wykonana, fragment kodu może uszkodzić system. Należy uważnie przeczytać kod źródłowy przed jego uruchomieniem.

    - Blok adresu URL pomocy fragment pliku może zawierać adresów URL, które wykonać pliku skryptu złośliwego lub wyświetlić obraźliwe witryny sieci Web.

    - Fragment kodu może zawierać odwołań, które są dodawane w trybie dyskretnym do projektu i mogą być ładowane z dowolnego miejsca w systemie. Te odwołania mogą została pobrana do komputera, z którego został pobrany fragment kodu. Fragment kodu może następnie wprowadzić wywołanie do metody w odwołaniu, która wykonuje złośliwego kodu. Aby zabezpieczyć się przed takimi atakami, przejrzyj bloki importów i odwołania do pliku fragmentu.

## <a name="see-also"></a>Zobacz także

[Visual Basic IntelliSense — wstawki programu](/dotnet/visual-basic/developing-apps/using-ide/intellisense-code-snippets)  
[Zabezpieczanie aplikacji](../ide/securing-applications.md)  
[Fragmenty kodu](../ide/code-snippets.md)