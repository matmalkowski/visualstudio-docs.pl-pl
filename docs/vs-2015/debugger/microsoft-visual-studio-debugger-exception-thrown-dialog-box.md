---
title: Microsoft Visual Studio Debugger (wystąpienie wyjątku), okno dialogowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.exceptions.thrown
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Microsoft Visual Studio Debugger (Exception Thrown) dialog box
- exception handling, during debugging
- debugger, exceptions
- throwing exceptions, during debugging
ms.assetid: 1fe98d10-c8f9-4b39-a920-99169bfd542e
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1d2b27620cbc37bd771fff364d06a1a33d9c8b07
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42683518"
---
# <a name="microsoft-visual-studio-debugger-exception-thrown-dialog-box"></a>Microsoft Visual Studio Debugger (wystąpienie wyjątku) ― okno dialogowe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [Microsoft Visual Studio Debugger (wystąpienie wyjątku), okno dialogowe](https://docs.microsoft.com/visualstudio/debugger/microsoft-visual-studio-debugger-exception-thrown-dialog-box).  
  
Wystąpił wyjątek w programach. To okno dialogowe Raporty rodzaj zgłaszanego wyjątku. Twój kod musi do obsługi tego wyjątku. Można wybrać jedną z następujących opcji do obsługi wyjątku:  
  
 **BREAK**  
 Zezwala na wykonywanie przerwać działanie debugera. Obsługa wyjątków nie jest wywoływany przed przerwy. Jeśli będziesz kontynuować z przerwy, zostanie wywołany program obsługi wyjątków.  
  
 **Continue**  
 Umożliwia wykonywanie kontynuować, dzięki czemu program obsługi wyjątków szansę, aby obsłużyć wyjątek. Ta opcja nie jest dostępna dla niektórych rodzajów wyjątków. **Kontynuuj** umożliwi aplikacji, aby kontynuować. W aplikacji macierzystej spowoduje wyjątek jest zgłaszany ponownie. W zarządzanej aplikacji albo spowoduje się program, aby zakończyć lub wyjątku, które mają być obsługiwane przez hostingu aplikacji.  
  
> [!NOTE]
>  Nie możesz kontynuować po wystąpieniu nieobsługiwanego wyjątku w kodzie zarządzanym. Wybieranie **Kontynuuj** po nieobsługiwany wyjątek w kodzie zarządzanym powoduje zatrzymanie debugowania.  
  
 **Ignoruj**  
 Zezwala na wykonywanie kontynuować bez wywoływania programu obsługi wyjątków. Ponieważ nie zostanie wywołany program obsługi wyjątków, może to prowadzić do dalsze konsekwencje, uwzględniając dodatkowe wyjątki i błędy. Ta opcja nie jest dostępna dla niektórych rodzajów wyjątków.  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie wyjątkami za pomocą debugera](../debugger/managing-exceptions-with-the-debugger.md)   
 [Najlepsze praktyki dotyczące wyjątków](http://msdn.microsoft.com/library/f06da765-235b-427a-bfb6-47cd219af539)   
 [Obsługa wyjątków](http://msdn.microsoft.com/library/ccb11fe8-6938-41ac-b477-a183e85865b9)



