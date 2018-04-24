---
title: 'Porady: znajdowanie DLL, która nastąpiła awaria programu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.dll
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, DLL crashes
- Module List dialog box
- errors [debugger], DLL crashes
- Modules window
- debugging [Visual Studio], DLL crashes
- DLLs, load order of
ms.assetid: ecf62568-8b65-4a41-b8a4-e962ff2dfb71
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 350cd8a78780eb8ddb2a197ed1e8920fda23bbf3
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-find-which-dll-your-program-crashed-in"></a>Porady: odnajdywanie biblioteki DLL, w której nastąpiła awaria programu
  
 Jeśli aplikacja ulegnie awarii podczas wywoływania biblioteki DLL systemu lub do kogoś innego kodu, należy znaleźć jaka DLL była aktywna podczas wystąpienia awarii. Jeśli wystąpi awaria w bibliotece DLL poza aplikacji użytkownika, można go zidentyfikować przy użyciu lokalizacji **modułów** okna.  
  
### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>Znajdź, w którym awaria wystąpił podczas korzystania z okna modułów  
  
1.  Należy pamiętać, adres, w których wystąpiła awaria.

    Jeśli adres nie jest wyświetlany w komunikacie o błędzie, może być konieczne alternatywne metody umożliwia zidentyfikowanie biblioteki DLL. Jeśli podejrzewasz systemowej biblioteki DLL, możesz [Załaduj symbole](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) z serwerów symboli firmy Microsoft podczas debugowania. W przeciwnym razie konieczne może być [Utwórz plik zrzutu](../debugger/using-dump-files.md) o stercie zamiast niego informacji. Różne [narzędzia](https://blogs.msdn.microsoft.com/andrehal/2009/12/31/what-is-a-dump-and-how-do-i-create-one/) są dostępne na potrzeby tworzenia plików zrzutu.
  
2.  Na **debugowania** menu, wybierz **Windows**i kliknij przycisk **modułów**.  
  
3.  W **modułów** oknie Znajdź **adres** kolumny. Konieczne może być umożliwia pasek przewijania jest widoczny.  
  
4.  Kliknij przycisk **adres** u góry kolumny, aby sortować według adresu bibliotek DLL.  
  
5.  Skanowanie posortowaną listę można znaleźć biblioteki DLL, której zakres adresów zawiera lokalizację awarii.  
  
6.  Przyjrzyj się **nazwa** i **ścieżki** kolumn, aby wyświetlić nazwę biblioteki DLL i ścieżkę.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie projektów DLL](../debugger/debugging-dll-projects.md)   
 [Porady: Korzystanie z okna modułów](../debugger/how-to-use-the-modules-window.md)