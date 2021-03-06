---
title: Komunikaty diagnostyczne w oknie danych wyjściowych | Dokumentacja firmy Microsoft
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
- vs.output
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- diagnostic messages [C#]
- System.Diagnostics.Debug class, Output window
- messages, diagnostic
- Debug.Print replacements
- diagnosis
- Output window, diagnostic messages
- System.Diagnostics.Trace class, Output window
- Trace class, diagnostic messages
- diagnostics
- debugger, Output window
- debugging [Visual Studio], diagnostic messages in Output window
- Debug class
ms.assetid: 386e9524-be17-4573-83fb-4f7c5cae0be0
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0a9e0bb4fa34133937e39b310cb05360e66a443
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42681874"
---
# <a name="diagnostic-messages-in-the-output-window"></a>Komunikaty diagnostyczne w oknie danych wyjściowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [komunikaty diagnostyczne w oknie danych wyjściowych](https://docs.microsoft.com/visualstudio/debugger/diagnostic-messages-in-the-output-window).  
  
Możesz zapisywać wiadomości w czasie wykonywania w oknie danych wyjściowych za pomocą klasy debugowania lub śledzenia, które są częścią <xref:System.Diagnostics> biblioteki klas. Korzystanie z klasy Debug, jeśli tylko dane wyjściowe w wersji debugowania programu. Jeśli chcesz, aby dane wyjściowe w wersji debugowania i wydania, użyj klasy Trace.  
  
## <a name="output-methods"></a>Metod wyjścia  
 <xref:System.Diagnostics.Trace> i <xref:System.Diagnostics.Debug> klasy zapewniają następujące metody dane wyjściowe:  
  
-   Różne `Write` metody, które dane wyjściowe informacji bez przerywania wykonywania. Te metody zamieniają `Debug.Print` metody używane w poprzednich wersjach programu Visual Basic.  
  
-   <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> i <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> metody, które przerwanie wykonywania i danych wyjściowych informacji określony warunek zakończy się niepowodzeniem. Domyślnie `Assert` metoda Wyświetla informacje w oknie dialogowym. Aby uzyskać więcej informacji, zobacz [potwierdzenia w kodzie zarządzany](../debugger/assertions-in-managed-code.md).  
  
-   <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName> i <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName> metody, które zawsze przerywa wykonywanie i wyświetla informacje o. Domyślnie `Fail` metody powodują wyświetlenie informacji w oknie dialogowym.  
  
 Oprócz programu się z aplikacji **dane wyjściowe** okna może wyświetlać informacje dotyczące:  
  
-   Modułów debuger został załadowany lub zwolnione.  
  
-   Wyjątki, które są zgłaszane.  
  
-   Procesy, które wyjść.  
  
-   Wątki, które wyjść.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Okno danych wyjściowych](../ide/reference/output-window.md)   
 [Śledzenie i Instrumentacja aplikacji](http://msdn.microsoft.com/library/773b6fc4-9013-4322-b728-5dec7a72e743)   
 [Wprowadzenie do Instrumentacji i śledzenia](http://msdn.microsoft.com/en-us/e924e57c-33cf-4b0e-9e7f-a45d13e38f2c)   
 [C#, F # i typów projektów języka Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Debugowanie zarządzanego kodu](../debugger/debugging-managed-code.md)



