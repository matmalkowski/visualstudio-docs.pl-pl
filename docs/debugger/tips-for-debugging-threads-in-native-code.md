---
title: Wskazówki dotyczące debugowanie wątków w kodzie natywnym | Dokumentacja firmy Microsoft
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
- threading [Visual Studio], debugging
- debugging [Visual Studio], threads
ms.assetid: 0374c8c6-57a3-4cfe-8047-2effef5ff5dc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: c98f6bb1a738111d32b26c5b923abe41367e621e
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="tips-for-debugging-threads-in-native-code"></a>Wskazówki dotyczące debugowanie wątków w kodzie natywnym
Poniżej przedstawiono kilka wskazówek, których można używać podczas debugowanie wątków w kodzie natywnym:  
  
-   Można wyświetlić zawartość blok informacji o wątku, wpisując `@TIB` w **czujki** okna lub **QuickWatch** okno dialogowe.  
  
-   Można wyświetlić kod ostatniego błędu dla bieżącego wątku, wprowadzając `@Err` w **czujki** okna lub **QuickWatch** okno dialogowe.  
  
-   Biblioteki wykonawcze języka C (CRT) funkcje mogą być przydatne w przypadku debugowanie aplikacji wielowątkowych. Aby uzyskać więcej informacji, zobacz [_malloc_dbg —](/cpp/c-runtime-library/reference/malloc-dbg).  
  
## <a name="see-also"></a>Zobacz też  
 [Debuguj aplikacje wielowątkowe](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)