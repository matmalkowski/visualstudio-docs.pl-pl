---
title: "Debugowanie w trybie mieszanym dla procesów IA64 nie jest obsługiwane. | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.interop_unsupported_ia64
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 20bc1e38-049b-4388-87c4-936815d85b46
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 193d469666d9aaa012187500de063470df77c823
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="mixed-mode-debugging-for-ia64-processes-is-unsupported"></a>Debugowanie w trybie mieszanym dla procesów IA64 nie jest obsługiwane.
Visual Studio nie obsługuje trybu mieszanego debugowania kodu zarządzanego i natywnego w procesów IA64. Oznacza to, że podczas debugowania nie można wykonać kroku z kodu zarządzanego do kodu natywnego lub kodu natywnego do zarządzanego kodu.  
  
### <a name="workarounds"></a>Rozwiązania  
  
-   Debugowanie kodu zarządzanego i natywnego w oddzielnych sesji debugowania.  
  
     —lub—  
  
     Debugowanie kodu mieszanych jako proces 32-bitowy, zgodnie z opisem w poniższych procedurach.  
  
### <a name="to-change-the-platform-to-32-bit-visual-basic-or-c"></a>Aby zmienić platformę 32-bitowych (Visual Basic lub C#)  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie kliknij przycisk **właściwości** w menu skrótów.  
  
2.  Na stronach właściwości, kliknij przycisk **skompilować** lub **debugowania** kartę.  
  
3.  Kliknij przycisk **platformy** i wybierz z listy platform x86.  
  
     Domyślnie domyślne Kompilatory języka Visual Basic i C# generuje kod, aby uruchomić na dowolnym Procesora. Na komputerze 64-bitowym tych plików binarnych Uruchom jako procesów 64-bitowych. Aby uruchomić proces 32-bitowy, musisz wybrać **Win32**, a nie **AnyCPU**.  
  
### <a name="to-change-the-platform-to-32-bit-cc"></a>Aby zmienić platformę 32-bitowych (C/C++)  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie kliknij przycisk **właściwości** w menu skrótów.  
  
2.  Na stronach właściwości, kliknij przycisk **platformy** i wybierz z listy platform, Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji 64-bitowych](../debugger/debug-64-bit-applications.md)