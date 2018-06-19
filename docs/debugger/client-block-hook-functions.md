---
title: Funkcje punktu zaczepienia bloku klienta | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- client blocks, validating and reporting data
- debugging [C++], hook functions
- _CrtSetDumpClient function
- client blocks, hook functions
- hooks, client block
ms.assetid: f21c197e-565d-4e3f-9b27-4c018c9b87fc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: eccc1781174394da333d2fc703fec0b4d31e522a
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31457234"
---
# <a name="client-block-hook-functions"></a>Funkcje punktu zaczepienia bloku klienta
Jeśli chcesz zweryfikować lub zgłosić zawartości danych przechowywanych w `_CLIENT_BLOCK` blokuje, można napisać funkcję specjalnie do tego celu. Funkcja, który można zapisać musi mieć prototyp podobny do następującego, zgodnie z definicją w CRTDBG. H:  
  
```  
void YourClientDump(void *, size_t)  
  
```  
  
 Innymi słowy, należy zaakceptować funkcji punktów zaczepienia **void** wskaźnika na początku bloku alokacji, wraz z **size_t** wpisz wartość wskazującą, rozmiar alokacji i zwracać `void`. Inną niż jego zawartość jest od użytkownika.  
  
 Po zainstalowaniu, używając funkcji punktów zaczepienia [_crtsetdumpclient —](/cpp/c-runtime-library/reference/crtsetdumpclient), będzie ona wywoływana zawsze `_CLIENT_BLOCK` bloku jest utworzyć zrzutu. Następnie można użyć [_crtreportblocktype —](/cpp/c-runtime-library/reference/crtreportblocktype) Aby uzyskać informacje na temat typu lub podtypu zrzut bloków.  
  
 Wskaźnik do funkcji, które są przekazywane do `_CrtSetDumpClient` jest typu **_crt_dump_client —**, zgodnie z definicją w CRTDBG. H:  
  
```  
typedef void (__cdecl *_CRT_DUMP_CLIENT)  
   (void *, size_t);  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie pisanie funkcji punktów zaczepienia](../debugger/debug-hook-function-writing.md)   
 [Przykładowe crt_dbg2](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)   
 [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype)