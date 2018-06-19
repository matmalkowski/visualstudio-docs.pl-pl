---
title: Wysyłać komunikaty diagnostyczne w oknie danych wyjściowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/25/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bfe7cb6660d16c093889395a082c9fd58e5d0431
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31474586"
---
# <a name="send-diagnostic-messages-to-the-output-window"></a>Wysyłać komunikaty diagnostyczne w oknie danych wyjściowych
Można pisać wiadomości środowiska wykonawczego **dane wyjściowe** przy użyciu okna `Debug` klasy lub `Trace` klasy, które wchodzą w skład z <xref:System.Diagnostics> biblioteki klas. Jeśli tylko dane wyjściowe w wersji do debugowania programu, należy użyć klasy debugowania. Klasa śledzenia należy użyć, jeśli dane wyjściowe w wersjach zarówno Debug i Release.  
  
## <a name="output-methods"></a>Dane wyjściowe metody  
 <xref:System.Diagnostics.Trace> i <xref:System.Diagnostics.Debug> klasy Podaj następujące dane wyjściowe metody:  
  
-   Różne `Write` metody, które zwracają informacje wynikowe bez przerywania wykonywania. Zastąp te metody `Debug.Print` metody używane w poprzednich wersjach programu Visual Basic.  
  
-   <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> i <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> metody, które podział informacji wykonywania i danych wyjściowych, gdy określony warunek nie powiedzie się. Domyślnie `Assert` metoda Wyświetla informacje w oknie dialogowym. Aby uzyskać więcej informacji, zobacz [potwierdzenia w kod zarządzany](../debugger/assertions-in-managed-code.md).  
  
-   <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName> i <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName> metody, które zawsze przerywa wykonywania i danych wyjściowych informacji. Domyślnie `Fail` metody wyświetlić informacje w oknie dialogowym.  
  
 Oprócz programu się z aplikacji **dane wyjściowe** okna może wyświetlać informacje o:  
  
-   Moduły debuger został załadowany lub zwalnianie modułu.  
  
-   Wyjątki, które są zgłaszane.  
  
-   Procesy, które wyjść.  
  
-   Wątki wyjść.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Okno danych wyjściowych](../ide/reference/output-window.md)   
 [Śledzenie i instrumentacja aplikacji](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)  
 [C#, F # i typy projektów Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Debugowanie zarządzanego kodu](../debugger/debugging-managed-code.md)