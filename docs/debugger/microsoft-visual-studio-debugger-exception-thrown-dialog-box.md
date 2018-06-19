---
title: Microsoft Visual Studio Debugger (wystąpienie wyjątku), okno dialogowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.exceptions.thrown
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Microsoft Visual Studio Debugger (Exception Thrown) dialog box
- exception handling, during debugging
- debugger, exceptions
- throwing exceptions, during debugging
ms.assetid: 1fe98d10-c8f9-4b39-a920-99169bfd542e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 24ccb3de6b22f54b239b5b772490a8d05a990dbd
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31475028"
---
# <a name="microsoft-visual-studio-debugger-exception-thrown-dialog-box"></a>Microsoft Visual Studio Debugger (wystąpienie wyjątku) ― okno dialogowe
Wystąpił wyjątek w programie. To okno dialogowe Raporty rodzaj został zwrócony wyjątek. Kod musi do obsługi tego wyjątku. Można wybrać jedną z następujących opcji obsługi wyjątku:  
  
 **Podziel**  
 Zezwala na wykonywanie można przerwać w debugerze. Program obsługi wyjątku nie jest wywoływany przed przerwy. Jeśli będziesz kontynuować z przerwy, zostanie wywołany program obsługi wyjątku.  
  
 **Continue**  
 Zezwala na wykonywanie kontynuować, zapewniając możliwość obsługi wyjątku obsługi wyjątków. Ta opcja nie jest dostępna dla niektórych typów wyjątków. **Kontynuować** umożliwi aplikacji, aby kontynuować. W aplikacji natywnej spowoduje zgłoszony wyjątek. W zarządzanej aplikacji albo spowoduje się program, aby zakończyć lub mają zostać obsłużone przez aplikację do obsługi wyjątku.  
  
> [!NOTE]
>  Nie można kontynuować po zakończeniu nieobsługiwany wyjątek w kodzie zarządzanym. Wybieranie **Kontynuuj** po nieobsługiwany wyjątek w kodzie zarządzanym powoduje zatrzymanie debugowania.  
  
 **Ignoruj**  
 Zezwala na wykonywanie kontynuować bez wywoływania obsługi wyjątków. Ponieważ program obsługi wyjątku nie jest wywoływany, może to prowadzić do dalsze konsekwencje, łącznie z dodatkowych wyjątków i błędów. Ta opcja nie jest dostępna dla niektórych typów wyjątków.  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie wyjątkami za pomocą debugera](../debugger/managing-exceptions-with-the-debugger.md)   
 [Najlepsze praktyki dotyczące wyjątków](/dotnet/standard/exceptions/best-practices-for-exceptions)   
 [Obsługa wyjątków](/cpp/windows/exception-handling-cpp-component-extensions)