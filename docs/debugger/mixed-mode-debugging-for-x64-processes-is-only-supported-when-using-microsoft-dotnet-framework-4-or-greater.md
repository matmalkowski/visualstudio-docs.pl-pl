---
title: "Tryb mieszany debugowania dla x64 procesów jest obsługiwana tylko w przypadku korzystania z programu Microsoft.NET Framework 4 lub nowszego | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.error.interop_unsupported_x64
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: b7495655-54c0-4315-8422-43bf63b8c22e
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 37d5c52192c30ccc3b34bfa609c3f6a7ffb99566
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="mixed-mode-debugging-for-x64-processes-is-only-supported-when-using-microsoftnet-framework-4-or-greater"></a>Debugowanie w trybie mieszanym dla procesów x64 jest obsługiwane tylko w przypadku korzystania z programu Microsoft .NET Framework 4 lub nowszej wersji
Platformę .NET framework w wersji starszej niż 4 nie zapewniają obsługę debugowanie w trybie mieszanym x64 procesów. Oznacza to, że podczas debugowania nie można wykonać kroku z kodu zarządzanego do kodu natywnego lub kodu natywnego do zarządzanego kodu.  
  
### <a name="workarounds"></a>Rozwiązania  
  
-   Aktualizowanie projektu do programu Microsoft .NET Framework 4 lub nowszy.  
  
     —lub—  
  
     Debugowanie kodu zarządzanego i natywnego w oddzielnych sesji debugowania.  
  
     —lub—  
  
     Debugowanie kodu mieszanych jako proces 32-bitowy, zgodnie z opisem w poniższych procedurach.  
  
### <a name="to-change-the-platform-to-32-bit-visual-basic-or-c"></a>Aby zmienić platformę 32-bitowych (Visual Basic lub C#)  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie kliknij przycisk **właściwości**.  
  
2.  Na stronach właściwości, kliknij przycisk **skompilować** lub **debugowania** kartę.  
  
3.  Kliknij przycisk **platformy** i wybierz z listy platform x86.  
  
     Domyślnie domyślne Kompilatory języka Visual Basic i C# generuje kod, aby uruchomić na dowolnym Procesora. Na komputerze 64-bitowym tych plików binarnych Uruchom jako procesów 64-bitowych. Aby uruchomić proces 32-bitowy, musisz wybrać **Win32**, a nie **AnyCPU**.  
  
### <a name="to-change-the-platform-to-32-bit-cc"></a>Aby zmienić platformę 32-bitowych (C/C++)  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie kliknij przycisk **właściwości**.  
  
2.  Na stronach właściwości, kliknij przycisk **platformy** i wybierz z listy platformy Win32.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Zobacz [Konfigurowanie debugowania SQL](http://msdn.microsoft.com/en-us/3db09e68-edcc-42de-9c22-4e97cfd55ab3).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji 64-bitowych](../debugger/debug-64-bit-applications.md)