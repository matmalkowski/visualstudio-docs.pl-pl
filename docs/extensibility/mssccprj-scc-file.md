---
title: MSSCCPRJ. Plik SCC | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, MSSCCPRJ.SCC file
- MSSCCPRJ.SCC file
ms.assetid: 6f2e39d6-b79d-407e-976f-b62a3cedd378
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 90a21ba6aafa0c5d06565c66531e2a6779aa419f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="mssccprjscc-file"></a>MSSCCPRJ. Plik SCC
Gdy Visual Studio rozwiązania lub projektu znajduje się pod kontrolą źródła przy użyciu środowiska IDE, IDE otrzymuje dwa kluczowych informacji z kontroli źródła wtyczek w postaci ciągów. Te ciągi "AuxPath" i "Nazwa_projektu.nazwa_modułu.nazwa_procedury", są nieprzezroczysta dla IDE, ale są one używane przez wtyczkę do zlokalizowania rozwiązania lub projektu w kontroli wersji. IDE zwykle uzyskuje te ciągi po raz pierwszy przez wywołanie metody [SccGetProjPath](../extensibility/sccgetprojpath-function.md), a następnie zapisuje je w pliku rozwiązania lub projektu dla przyszłych połączeń w celu [SccOpenProject](../extensibility/sccopenproject-function.md). Osadzone w pliki rozwiązań i projektów ciągi "AuxPath" i "Nazwa_projektu.nazwa_modułu.nazwa_procedury" nie są automatycznie aktualizowane podczas użytkownika gałęzi rozwidlenia, albo kopiuje pliki rozwiązań i projektów, które znajdują się w kontroli wersji. Aby upewnić się, że pliki rozwiązań i projektów wskazują ich poprawnej lokalizacji w kontroli wersji, należy ręcznie zaktualizować ciągi. Ponieważ ciągi mają być nieprzezroczyste, jego mogą nie być wyczyść jak powinny być zaktualizowane.  
  
 Wtyczka do kontroli źródła można uniknąć tego problemu przez przechowywanie ciągów "AuxPath" i "Nazwa_projektu.nazwa_modułu.nazwa_procedury" w specjalny plik o nazwie MSSCCPRJ. Plik SCC. Jest to plik lokalnego, po stronie klienta jest własnością i obsługiwanego przez wtyczkę. Ten plik nigdy nie jest umieszczone pod kontrolą źródła, ale jest generowany przez wtyczkę dla każdego katalogu, który zawiera pliki pod kontrolą źródła. Aby ustalić, które pliki są pliki rozwiązań i projektów programu Visual Studio, wtyczka do kontroli źródła można porównać rozszerzenia pliku z listą standard lub dostarczone przez użytkownika. Po IDE wykrywa, że wtyczka obsługuje MSSCCPRJ. Plik SCC przestaje osadzić "AuxPath" i "Nazwa_projektu.nazwa_modułu.nazwa_procedury" ciągów do rozwiązania i pliki projektu i odczytuje te ciągi z MSSCCPRJ. SCC plików zamiast tego.  
  
 Wtyczka do kontroli źródła obsługującego MSSCCPRJ. Plik SCC musi być zgodne z następującymi zasadami:  
  
-   Może istnieć tylko jeden MSSCCPRJ. SCC plików dla katalogu.  
  
-   MSSCCPRJ. Plik SCC może zawierać "AuxPath" i "Nazwa_projektu.nazwa_modułu.nazwa_procedury", w przypadku wielu plików, które są pod kontrolą źródła w podanym katalogu.  
  
-   Ciąg "AuxPath" nie może mieć cudzysłowy wewnątrz niej. Może mieć stawiać cudzysłów wokół go jako ograniczników (na przykład para podwójnych cudzysłowów służy do wskazać ciągiem pustym). IDE usuwa wszystkie oferty z ciągu "AuxPath" przeczytaniu z MSSCCPRJ. Plik SCC.  
  
-   Ciąg "Nazwa_projektu.nazwa_modułu.nazwa_procedury" w MSSCCPRJ. Plik SCC musi odpowiadać dokładnie ciąg zwrócony `SccGetProjPath` funkcji. Jeśli długość ciągu zwróconego przez funkcję ma cudzysłowów wokół niego ciąg w MSSCCPRJ. Plik SCC musi mieć cudzysłowów wokół niego i na odwrót.  
  
-   MSSCCPRJ. SCC pliku jest tworzony lub aktualizowany w każdym przypadku, gdy plik jest umieszczone pod kontrolą źródła.  
  
-   Jeśli moduł MSSCCPRJ. Plik SCC zostaje usunięta, dostawcy należy ponownie wygenerować go następnym wykonuje operację na kontroli źródła dotyczące tego katalogu.  
  
-   MSSCCPRJ. Plik SCC ściśle musi mieć format zdefiniowany.  
  
## <a name="an-illustration-of-the-mssccprjscc-file-format"></a>Ilustracja MSSCCPRJ. Format pliku SCC  
 Poniżej przedstawiono przykładowe MSSCCPRJ. Format pliku SCC (numery wierszy są udostępniane tylko jako wskazówki i nie powinny znajdować się w treści pliku):  
  
 [Wiersza 1]`SCC = This is a Source Code Control file`  
  
 [Wiersz 2]  
  
 [Wiersz 3]`[TestApp.sln]`  
  
 [Wiersz: 4]`SCC_Aux_Path = "\\server\vss\"`  
  
 [Wiersz 5]`SCC_Project_Name = "$/TestApp"`  
  
 [Wiersz: 6]  
  
 [Wiersz 7]`[TestApp.csproj]`  
  
 [Wiersz: 8]`SCC_Aux_Path = "\\server\vss\"`  
  
 [Wiersz 9]`SCC_Project_Name = "$/TestApp"`  
  
 Pierwszy wiersz stany zastosowanie pliku i służy jako podpis dla wszystkich plików tego typu. Ten wiersz powinien pojawić się dokładnie tak jak poniżej w MSSCCPRJ wszystkie. Pliki SCC:  
  
 `SCC = This is a Source Code Control file`  
  
 Występuje po sekcji ustawień dla każdego pliku, który jest oznaczony jako nazwę pliku w nawiasach kwadratowych. W tej sekcji jest powtarzane dla każdego pliku śledzenia. Ten wiersz jest przykładowe nazwy pliku, a mianowicie, `[TestApp.csproj]`. IDE oczekuje następujące dwa wiersze. Nie, jednak definiuje styl wartości zdefiniowane. Zmienne są `SCC_Aux_Path` i `SCC_Project_Name`.  
  
 `SCC_Aux_Path = "\\server\vss\"`  
  
 `SCC_Project_Name = "$/TestApp"`  
  
 Nie ma ustawionego ogranicznika zakończenia w tej sekcji. Nazwa pliku, a także wszystkie literały, które pojawiają się w pliku są zdefiniowane w pliku nagłówka scc.h. Aby uzyskać więcej informacji, zobacz [ciągi używane jako klucze do znajdowania Plug-in kontroli źródła](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Plug-in kontroli źródła](../extensibility/source-control-plug-ins.md)   
 [Ciągi używane jako klucze do znajdowania wtyczki kontroli źródła](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)