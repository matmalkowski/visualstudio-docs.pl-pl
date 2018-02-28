---
title: Techniki debugowania CRT | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.runtime.debugging
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [CRT]
- CRT, debugging
- debugging [C++], CRT debug support
ms.assetid: 9be561f6-14a8-44ff-925d-d911d5b8e6ff
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 52f1847112741e90634ce0e68acbcfdd11b837db
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="crt-debugging-techniques"></a>Techniki testowania CRT
Jeśli debugowany program, który korzysta z biblioteki wykonawcze języka C, mogą być przydatne tych metod debugowania.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Korzystanie z biblioteki debugowania CRT](../debugger/crt-debug-library-use.md)  
 W tym artykule opisano obsługę debugowania pochodzącymi z biblioteki wykonawczej języka C i instrukcje na temat uzyskiwania dostępu do narzędzi.  
  
 [Makra raportowania](../debugger/macros-for-reporting.md)  
 Zawiera informacje na temat **_rptn —** i **_rptfn —** makra (zdefiniowany w CRTDBG. H), których użycie `printf` instrukcje do debugowania.  
  
 [Wersja debugowania funkcji alokacji sterty](../debugger/debug-versions-of-heap-allocation-functions.md)  
 W tym artykule omówiono specjalnych wersji debugowania funkcji alokacji sterty, w tym: jak CRT mapuje wywołań, zalet wywoływania je jawnie, jak uniknąć konwersji śledzenia oddzielne typy alokacji w blokach klienta i wyniki nie definiuje _ DEBUGOWANIA.  
  
 [Szczegóły dotyczące sterty debugowania CRT](../debugger/crt-debug-heap-details.md)  
 Zawiera łącza do zarządzania pamięcią i sterty debugowania, typy bloków na stercie debugowania przy użyciu sterty debugowania, stanu sterty funkcje raportowania i śledzenie żądań alokacji stosu.  
  
 [Debugowanie pisanie funkcji punktów zaczepienia](../debugger/debug-hook-function-writing.md)  
 Utworzenie punktu zaczepienia list łącza do bloku klienta, funkcji, funkcji punktów zaczepienia alokacji punkty zaczepienia alokacji i alokacji pamięci CRT i raportowanie funkcji punktów zaczepienia.  
  
 [Wyszukiwanie przecieków pamięci za pomocą biblioteki CRT](../debugger/finding-memory-leaks-using-the-crt-library.md)  
 Obejmuje techniki wykrywanie i izolowanie przecieków pamięci za pomocą debugera i biblioteki wykonawczej języka C.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)  
 W tym artykule omówiono niektóre typowe problemy debugowania i techniki aplikacji C i C++.  
  
 [Zabezpieczenia debugera](../debugger/debugger-security.md)  
 Zawiera zalecenia dotyczące debugowania bardziej bezpieczne.