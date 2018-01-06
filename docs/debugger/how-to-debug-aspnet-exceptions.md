---
title: "Porady: debugowanie wyjątków ASP.NET | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], ASP.NET exceptions
- ASP.NET, exceptions
- exceptions, ASP.NET
ms.assetid: 1810096e-de8c-435e-be3d-f365d0cd0a6a
caps.latest.revision: "23"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: aspnet
ms.openlocfilehash: 82c81f2998497f047550e35397dc870338ed977e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-debug-aspnet-exceptions"></a>Porady: debugowanie wyjątków ASP.NET
Debugowanie wyjątkami jest ważną częścią tworzenie niezawodnych [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji. Informacje ogólne o tym, jak można debugować wyjątki znajduje się na [Zarządzanie wyjątkami za pomocą debugera](../debugger/managing-exceptions-with-the-debugger.md).  
  
 Aby debugować nieobsługiwany [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] wyjątki, należy się upewnić, że debuger zatrzymuje dla nich. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Środowiska uruchomieniowego ma obsługi wyjątków najwyższego poziomu. W związku z tym debuger nigdy nie dzieli w przypadku nieobsługiwanych wyjątków domyślnie. Aby przerwać w debugerze, gdy jest zgłaszany wyjątek, należy wybrać **Przerwij, gdy jest wyjątek: zgłoszono** ustawienie wyjątek w **wyjątki** okno dialogowe.  
  
 Jeśli włączono opcję tylko mój kod, **Przerwij, gdy jest wyjątek: zgłoszono** nie powoduje, że debuger przerwanie natychmiast, jeśli wyjątek w metodzie .NET Framework lub inny kod systemu. Zamiast tego wykonywania kontynuowany do momentu debuger trafienia kodu z systemem innym niż system, a następnie przerywa. W związku z tym nie ma kroków kodu systemu po wystąpieniu wyjątku.  
  
 Tylko mój kod umożliwia innym rozwiązaniem, które mogą być przydatne bardziej: **Przerwij, gdy jest wyjątek: nieobsługiwany użytkownika**. Jeśli to ustawienie dla wyjątku, debuger będzie przerwać wykonywanie w kodzie użytkownika tylko wtedy, gdy wyjątek nie jest przechwycony i obsługiwane przez kod użytkownika. To ustawienie Negacja efekt najwyższego poziomu [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] program obsługi wyjątku, ponieważ jest programu obsługi kodu innych użytkowników.  
  
### <a name="to-enable-debugging-of-aspnet-exceptions-with-just-my-code"></a>Aby włączyć debugowanie wyjątków ASP.NET z tylko mój kod  
  
1.  Na **debugowania** menu, kliknij przycisk **wyjątki**.  
  
     **Wyjątki** zostanie wyświetlone okno dialogowe.  
  
2.  Na **wspólnego języka środowiska uruchomieniowego wyjątki** wierszu, wybierz opcję **wyrzuconych** lub **nieobsługiwanych przez użytkownika**.  
  
     Aby użyć **nieobsługiwanych przez użytkownika** ustawienie, **tylko mój kod** musi być włączona...  
  
### <a name="to-use-best-practices-for-aspnet-exception-handling"></a>Aby stosować najlepsze rozwiązania dla obsługi wyjątków ASP.NET  
  
-   Miejsce `try ... catch` bloki wokół kod, który może zgłaszać wyjątki można przewidzieć i informacji o sposobie obsługi. Na przykład jeśli aplikacja jest wykonywania wywołań do usługi XML sieci Web lub bezpośrednio do programu SQL Server, że kod powinien być w **try... catch** blokuje, ponieważ istnieje wiele wyjątków, które mogą wystąpić.

## <a name="see-also"></a>Zobacz też
[Debugowanie aplikacji ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)