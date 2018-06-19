---
title: JIT Optymalizacja i debugowanie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], optimized code
- optimized code, debugging
ms.assetid: 19bfabf3-1a2e-49dc-8819-a813982e86fd
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9a9b18ab38c7c19fa5208d34439bd3133099e8bc
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31477358"
---
# <a name="jit-optimization-and-debugging"></a>Optymalizacja i debugowanie JIT
**Jak działają funkcje optymalizacji programu .NET:** Jeśli próbujesz debugowania kodu, łatwiej gdy kod jest **nie** zoptymalizowane. To dlatego, jeśli kod jest zoptymalizowany, kompilatora i środowiska uruchomieniowego dokonać zmian emitowany kodu procesora CPU, aby działa szybciej, ale ma mniej bezpośredniego mapowania do oryginalnego kodu źródłowego. Oznacza to, że debugery są często informujące wartości zmiennych lokalnych i kodu wykonywanie krok po kroku, a punkty przerwania może nie działać zgodnie z oczekiwaniami.

Zwykle konfigurację kompilacji wydania tworzy zoptymalizowanego kodu i nie obsługuje konfiguracji kompilacji debugowania. `Optimize` Właściwość MSBuild Określa, czy kompilator jest informację do optymalizacji kodu.

W ekosystemie .NET kodu jest włączona ze źródła do instrukcji procesora CPU w dwóch etapach: najpierw kompilatora C# konwertuje tekst wprowadzony w postaci binarnej pośredniej o nazwie MSIL i zapisuje ten plików dll. Później środowisko uruchomieniowe platformy .NET konwertuje to MSIL do instrukcji procesora CPU. W pewnym stopniu można zoptymalizować w obu czynności, ale bardziej znaczących optymalizacje wykonuje drugi etap wykonywane przez środowisko uruchomieniowe platformy .NET.

**Opcja "Pomiń optymalizację JIT podczas ładowania modułu (tylko kod zarządzany)":** debuger udostępnia opcję, która kontroluje, co się stanie po ładuje bibliotekę DLL, która jest skompilowany z włączonymi optymalizacjami wewnątrz procesu docelowego. Jeśli ta opcja jest zaznaczona (stan domyślny), a następnie środowiska uruchomieniowego .NET kompiluje kod MSIL do kodu procesora CPU, pozostawia włączonymi optymalizacjami. Jeśli opcja jest zaznaczona, debuger żąda wyłączone optymalizacje.

**Pomiń optymalizację JIT podczas ładowania modułu (tylko kod zarządzany)** opcji można znaleźć w **ogólne** w obszarze **debugowanie** w węźle **opcje** okno dialogowe.

**Kiedy należy zaznaczysz tę opcję:** zaznaczeniu tej opcji w przypadku bibliotek DLL są pobierane z innego źródła, takie jak pakietu nuget debugować kod w tej biblioteki DLL. Aby to zrobić można również znaleźć pliku symboli (.pdb) dla tej biblioteki DLL.

Jeśli interesuje Cię tylko debugowanie kodu, które tworzysz lokalnie, najlepiej pozostawić ta opcja nie jest zaznaczona, ponieważ w niektórych przypadkach włączenie tej opcji będzie znacznie spowolnić debugowania. Istnieją dwa przyczyna to spowolnić:

* Kod zoptymalizowany działa szybciej. Jeśli są wyłączenie optymalizacji dla części kodu, można sumują wpływu na wydajność.
* Jeśli masz tylko mój kod włączone debuger nawet spróbuj i załadować symbole dla bibliotek DLL, które są zoptymalizowane. Znajdowanie symboli może zająć dużo czasu.

**Ograniczenia dotyczące tej opcji:** istnieją dwie sytuacje, gdy ta opcja spowoduje **nie** pracy:

1. W sytuacjach, w którym są dołączanie debugera do już uruchomionego procesu ta opcja nie wpłyną na modułów, które zostały już załadowane w czasie, który debuger został dołączony.
2. Ta opcja nie ma wpływu na bibliotek DLL, które zostały wstępnie skompilowanych do natywnego kodu (nazywane również przetworzone przez program ngen). Można jednak wyłączyć użycia wstępnie skompilowany kod, przez uruchomienie procesu ze środowiskiem zmiennej COMPlus_ZapDisable ustawiony na "1".

## <a name="see-also"></a>Zobacz też  
 [Debugowanie zarządzanego kodu](../debugger/debugging-managed-code.md)   
 [Nawigowanie po kodzie za pomocą debugera](../debugger/navigating-through-code-with-the-debugger.md)   
 [Dołączanie do uruchomionego procesu](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Proces zarządzanego wykonania](/dotnet/standard/managed-execution-process)
