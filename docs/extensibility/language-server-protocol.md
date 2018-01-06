---
title: "Omówienie protokołu Server języka | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/14/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a7d93c2-31ea-4bae-8b29-6988a567ddf2
caps.latest.revision: "1"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 79022af292161d30440a01749ecc929ce7f3b511
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="language-server-protocol"></a>Protokół serwera języka

## <a name="what-is-the-language-server-protocol"></a>Co to jest protokół serwera języka?

Kod źródłowy auto zakończeń obsługi zaawansowanej edycji funkcji, takich jak lub **przejdź do definicji** język programowania w IDE lub edytora jest zazwyczaj bardzo trudne i czasochłonna. Zazwyczaj wymaga zapisywania modelu domeny (skaner, analizatora składni, sprawdzanie typu, konstruktora i inne) w języku programowania IDE lub edytora. Na przykład wtyczka czasu CDT Eclipse, która zapewnia obsługę dla C/C++ w środowisku Eclipse IDE jest napisane w języku Java, ponieważ sam IDE Eclipse jest napisany w języku Java. Następujące takie podejście oznaczałoby to implementacja modelu domeny C/C++ w TypeScript dla Visual Studio Code oraz modelu osobnej domenie w języku C# dla programu Visual Studio.

Tworzenie modeli domeny specyficzny dla języka są znacznie łatwiejsze, jeśli narzędzie programistyczne można ponownie użyć istniejącej biblioteki specyficzny dla języka. Jednak te biblioteki zwykle są implementowane w języku programowania sam (na przykład dobrej C/C++ domeny modeli są zaimplementowane w języku C/C++). Integrowanie biblioteki C/C++ do edytora zapisywane na maszynie jest technicznie możliwe, ale twardych zrobić.

### <a name="language-servers"></a>Serwery języka

Innym rozwiązaniem jest uruchomienie biblioteki we własnym procesie i użyj komunikacji międzyprocesowej do komunikowania się do niego. Komunikaty wysyłane do i z powrotem tworzą protokołu. Protokół serwera języka (LSP) jest iloczyn standaryzacji wiadomości wymieniane między narzędzie do projektowania i proces serwera języka. Przy użyciu języka serwerów lub demons nie jest rozwiązaniem w nowych lub nowej. Edytory, takich jak Vim i Emacs ma został w ten sposób przez pewien czas zapewnić obsługę semantycznego Autouzupełniania. Celem LSP było uprościć tego rodzaju integracji i zapewnienia przydatne framework udostępnianie funkcje języka aby różnych narzędzi.

Mających wspólny protokół umożliwia integrację programowania — funkcje językowe do narzędzia programowanie z minimalnym problemów przez ponowne użycie z istniejącej implementacji języka modelu domeny. Język serwera zaplecza może być napisane w PHP, Python lub Java i LSP umożliwia mu można łatwo zintegrować różnych narzędzi. Protokół działa na wspólnej poziomie abstrakcji tak, aby narzędzie zaoferować bogaty język usługi bez konieczności pełni poznać wszystkie szczegóły specyficzne dla źródłowego modelu domeny.

## <a name="how-work-on-the-lsp-started"></a>Jak działają na LSP uruchomiona

LSP powstał w czasie, a obecnie jest w wersji 3.0. Jego uruchomienia, gdy pojęcia języka serwera została pobrana przez OmniSharp do zapewnienia rozbudowane funkcje edycji C#. Początkowo OmniSharp używać protokołu HTTP z ładunek JSON i zostało zintegrowane kilka edytory tym [Visual Studio Code](https://code.visualstudio.com).

Zbliżonym do czasu Microsoft zaczęła działać na serwerze języka TypeScript, z myślą o obsługi języka TypeScript w edytorach, takich jak Emacs i Sublime Text. W tej implementacji edytora komunikuje się za pośrednictwem stdin/stdout z procesu serwera TypeScript i używa przez protokół debugera V8 ładunek JSON dla żądań i odpowiedzi. Serwer TypeScript zostało zintegrowane wtyczki TypeScript Sublime i kodzie VS do edycji sformatowanego maszynie.

Po w zintegrowanym dwa serwery z inną wersją językową, kodzie VS team rozpoczął Eksploruj edytory i IDEs wspólny protokół serwera języka. Wspólny protokół umożliwia dostawcy języka utworzyć serwer jednego języka, który może być zużyte przez różne IDEs. Aby zaimplementować jeden raz po stronie klienta protokołu ma tylko konsumenta serwera języka. Powoduje to sytuacja win-win dla dostawcy języka i konsumentów języka.

Wprowadzenie do protokołu języka używanego przez serwer TypeScript, było więcej ogólne i niezależne od języka. Protokół została wykonana z użyciem więcej funkcji języka przy użyciu języka VS kodu interfejsu API dla pomysłów. Samego protokołu jest wspierany przez usługę RPC JSON dla zdalnego wywołania z powodu jego bibliotek prostoty i obsługa wielu języków programowania.

Dogfooded zespołu kodzie VS protokołu implementując kilka serwerów języka linter. Serwer języka linter odpowiada na żądania wierszu (skanowanie) pliku i zwraca zestaw elementów wykrytych ostrzeżeń i błędów. Celem było wierszu pliku jako użytkownika zmiany w dokumencie, co oznacza, że będzie wiele żądań linting podczas sesji przy użyciu edytora. On warto zachować serwera i systemem tak, aby nowy proces linting nie musiały zostać uruchomione dla każdej Edycja użytkownika. Kilka serwerów linter zostały wprowadzone w tym kodzie VS ESLint i TSLint rozszerzeń. Tych dwóch serwerów linter zarówno implementowanych w TypeScript/JavaScript i uruchom na Node.js. Ich udostępnianie biblioteki, która implementuje na kliencie i serwerze część protokołu.

## <a name="how-the-lsp-works"></a>Jak działa LSP

Serwer języka działa we własnym procesie i narzędzi, takich jak Visual Studio lub kodzie VS komunikacji z serwerem za pośrednictwem wywołania RPC JSON przy użyciu protokołu języka. Inną zaletą operacyjnego w dedykowanym procesie serwera języka to uniknąć problemów z wydajnością związane z modelem jednego procesu. Kanał transportu rzeczywiste może być stdio —, gniazda, nazwane potoki lub ipc węzła Jeśli klienta i serwera są zapisywane w środowisku Node.js.

Poniżej jest przykładem narzędzie a serwerem języka komunikowania się podczas procedury sesji edytowania:

![diagram przepływu LSP](media/lsp-flow-diagram.png)

* **Użytkownik otwiera plik (określone jako dokument) w narzędziu**: narzędzie powiadamia serwer języka, że dokument jest otwarty ("textDocument/didOpen"). Odtąd prawdy o zawartości dokumentu nie jest już w systemie plików, ale przechowywane przez narzędzie w pamięci.

* **Użytkownik nie wybrał edycji**: narzędzie informuje serwer o zmianie dokumentu ("textDocument/didChange") i informacje semantyczne programu został zaktualizowany przez serwer języka. Dzieje się tak, serwer języka analizy te informacje i powiadamia narzędzie z wykryto błędy i ostrzeżenia ("textDocument/publishDiagnostics").

* **Użytkownik wykonuje "Przejdź do definicji" na symbol w edytorze**: narzędzie wysyła żądanie "textDocument/definicji" dwa parametry: (1) (2 położenie tekstu, z której zainicjowano przejdź do definicji żądania do serwera i dokumentów identyfikatora URI. Serwer odpowiada, podając identyfikator URI dokumentu i położenie definicji symbolu w dokumencie.

* **Użytkownik zamyka dokument (plik)**: narzędzie dowie się, że dokument jest teraz już w pamięci, który bieżącą zawartość jest teraz na bieżąco w systemie plików serwera języka jest wysyłane powiadomienie "textDocument/didClose".

W tym przykładzie pokazano, jak protokół komunikuje się z serwerem języka na poziomie funkcji edytora, takich jak "Przejdź do definicji", "Znajdź wszystkie odwołania". Typy danych używanych przez protokół są edytora lub IDE "typów danych", takich jak dokument tekstowy aktualnie otwarty i pozycji kursora. Typy danych nie są na poziomie modelu domeny języka programowania, który zapewni zwykle drzewa składni abstrakcyjnej i symbole kompilatora (na przykład rozpoznać typy, przestrzenie nazw,...). Znacznie ułatwia protokołu.

Teraz Przyjrzyjmy się żądania "textDocument/definicji" bardziej szczegółowo. Poniżej przedstawiono ładunków, które przejść między narzędziem klienta i serwera języka dla żądania "Przejdź do definicji" w dokumencie języka C++.

Jest to żądanie:

```json
{
    "jsonrpc": "2.0",
    "id" : 1,
    "method": "textDocument/definition",
    "params": {
        "textDocument": {
            "uri": "file:///p%3A/mseng/VSCode/Playgrounds/cpp/use.cpp"
        },
        "position": {
            "line": 3,
            "character": 12
        }
    }
}
```

To jest odpowiedź:

```json
{
    "jsonrpc": "2.0",
    "id": "1",
    "result": {
        "uri": "file:///p%3A/mseng/VSCode/Playgrounds/cpp/provide.cpp",
        "range": {
            "start": {
                "line": 0,
                "character": 4
            },
            "end": {
                "line": 0,
                "character": 11
            }
        }
    }
}
```

W retrospect opisujący typy danych na poziomie edytora, a nie na poziomie modelu język programowania jest jednym z powodów Powodzenie protokół serwera języka. Jest znacznie prostsza do normalizacji dokument tekstowy identyfikatora URI lub pozycji kursora w porównaniu z standaryzacji składni abstrakcyjnej drzewa kompilatora symbole w różnych językach programowania.

Podczas pracy z różnych języków, VS zwykle zaczyna się kod języka serwera dla każdego języka programowania. W poniższym przykładzie pokazano sesji, gdy użytkownik pracuje z języka Java i SASS plików.

![Java i sass](media/lsp-java-and-sass.png)

### <a name="capabilities"></a>Możliwości

Nie wszystkie serwery język może obsługiwać wszystkie funkcje zdefiniowane przez protokół. W związku z tym klientem i serwerem ogłasza ich zestaw funkcji obsługiwanych przez "funkcji". Na przykład serwer informuje, że może obsłużyć żądania "textDocument/definicji", ale go nie może obsłużyć żądania "obszaru roboczego/symbol". Podobnie klienci ogłaszamy się możliwość zapewnienia "około można zapisać" powiadomienia przed zapisaniem dokumentu, dzięki czemu serwer może obliczeniowe tekstową edycji można automatycznie sformatować dokumentu edytowanego.

## <a name="integrating-a-language-server"></a>Integracja serwera języka

Rzeczywiste integracji serwera języka do określonego narzędzia nie jest zdefiniowana przez protokół serwera języka i pozostaje implementors narzędzia. Niektóre narzędzia integracji serwerów języka objęty przez rozszerzenie, które można uruchomić i zwróć się do dowolnego rodzaju języka serwera. Innych osób, takich jak kodzie VS utworzyć niestandardowego rozszerzenia na serwer języka, aby rozszerzenie jest nadal w stanie dostarczyć niektóre funkcje niestandardowe języka.

Aby uprościć implementacji języka serwerów i klientów, znajdują się biblioteki lub zestawów SDK składników klienta i serwera. Te biblioteki są dostępne dla różnych języków. Na przykład istnieje [moduł npm klienta języka](https://www.npmjs.com/package/vscode-languageclient) do włączenia serwera języka do rozszerzenia kodzie VS i drugą do jej obsługi ułatwiają [moduł npm serwera języka](https://www.npmjs.com/package/vscode-languageserver) zapisu języka serwera przy użyciu środowiska Node.js. To jest bieżący [listy](https://github.com/Microsoft/language-server-protocol/wiki/Protocol-Implementations) bibliotek pomocy technicznej.

## <a name="using-the-language-server-protocol-in-visual-studio"></a>Przy użyciu protokołu serwera języka w programie Visual Studio

* [Dodawanie rozszerzenia protokołu serwera języka](adding-an-lsp-extension.md) — Dowiedz się więcej o integracji serwera języka Visual Studio.
