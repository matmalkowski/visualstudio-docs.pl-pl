---
title: Debugowanie zarządzanego kodu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging managed code
- debugging ASP.NET Web applications, managed code
- managed code, debugging
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 8d7bb0c18eda3f8bb4d5387acdcf496e204f8018
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="debugging-managed-code"></a>Debugowanie zarządzanego kodu

W tej sekcji opisano typowe problemy debugowania i techniki zarządzanych aplikacji lub aplikacje napisane w językach kierowanych środowiska CLR, takich jak Visual Basic, C# i C++. Techniki opisane w tym miejscu są techniki wysokiego poziomu. Aby uzyskać więcej informacji, zobacz [korzystanie z debugera](../debugger/debugger-basics.md).

## <a name="in-this-section"></a>W tej sekcji

[Komunikaty diagnostyczne w oknie danych wyjściowych](../debugger/diagnostic-messages-in-the-output-window.md)  
W tym artykule opisano <xref:System.Diagnostics.Debug> i <xref:System.Diagnostics.Trace> klasy, z którymi może zapisywać komunikaty czasu wykonywania, aby **dane wyjściowe** okna. Te klasy obejmują dane wyjściowe metody, umożliwiających informacji wyjściowych bez przerywania wykonywania i informacje o danych wyjściowych, który również powoduje przerwanie wykonywania, jeśli określony warunek nie powiedzie się.

[Potwierdzenia w zarządzanym kodzie](../debugger/assertions-in-managed-code.md)  
W tym artykule opisano potwierdzenia w zarządzanym kodzie, których warunki określające jako argumenty do badania `Assert` metody. Ponadto, w tym temacie przedstawiono przykładowy kod informacji na temat używania <xref:System.Diagnostics.Debug> i <xref:System.Diagnostics.Trace> metody klasy, zagadnienia dotyczące wersji debugującej i zwalniającej kodu, efekty uboczne assert argumentów, dostosowywanie assert zachowanie i plików konfiguracji.

[Instrukcje stop w Visual Basic](../debugger/stop-statements-in-visual-basic.md)  
W tym artykule opisano `Stop` instrukcja, która stanowi alternatywę dla ustawienia punktu przerwania. Przykładowy kod jest również udostępniany, wraz z porównanie `Stop` instrukcji i `End` instrukcji, jak również między `Stop` i `Assert` instrukcji.

[Przewodnik: debugowanie formularza Windows Forms](../debugger/walkthrough-debugging-a-windows-form.md)  
Zapewnia instrukcje krok po kroku dotyczące tworzenia formularzy systemu Windows i debugowanie tego formularza. Formularz systemu Windows, standardowy składnik zarządzanych aplikacji systemu Windows, jest jednym z najbardziej typowych zarządzanych aplikacji. W tym przewodniku zastosowano Visual C# i Visual Basic, ale zazwyczaj przypominają techniki tworzenia formularzy systemu Windows w języku C++.

[Debugowanie metody OnStart](../debugger/how-to-debug-the-onstart-method.md)  
Zawiera przykłady kodu, co pozwala na debugowanie `OnStart` metody zarządzanych usług systemu Windows. Aby debugować `OnStart` metody usługi systemu Windows, należy dodać kilka wierszy kodu w celu symulowania usługi.

[Debugowanie w trybie mieszanym](../debugger/debugging-mixed-mode-applications.md)  
W tym artykule omówiono debugowanie trybu mieszanego aplikacji. Oznacza to, każda aplikacja, która łączy kodu natywnego z kodu zarządzanego.

[Błąd: Debugowanie nie jest możliwe, ponieważ debuger jądra został wyłączony z poziomu systemu](../debugger/error-debugging-isn-t-possible-because-a-kernel-debugger-is-enabled-on-the-system.md)  
W tym artykule opisano komunikat o błędzie, który występuje podczas debugowania kodu zarządzanego na [!INCLUDE[win7](../debugger/includes/win7_md.md)], [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)], [!INCLUDE[winxp](../code-quality/includes/winxp_md.md)], [!INCLUDE[Win2kFamily](../code-quality/includes/win2kfamily_md.md)], lub systemu Windows NT, który został uruchomiony w trybie debugowania.

[Optymalizacja i debugowanie JIT](../debugger/jit-optimization-and-debugging.md)  
Opis skutków optymalizację JIT na debugowanie.

[Debugowanie LINQ i DLINQ](../debugger/debugging-linq.md)  
W tym artykule omówiono techniki debugowania zapytań LINQ.

[Wskazówki: Debugowanie aplikacji równoległych](../debugger/walkthrough-debugging-a-parallel-application.md)  
Informacje dotyczące używania **zadań równoległych** i **stosów równoległych** narzędzia systemu windows do debugowania aplikacji równoległych.

## <a name="related-sections"></a>Sekcje pokrewne

[IntelliTrace](../debugger/intellitrace.md) znaleźć usterki szybciej i łatwiej przez rejestrowanie historii wykonywania aplikacji przy użyciu funkcji IntelliTrace. Krok wstecz i przekazywać je za pomocą wywołań sprawdzać stan aplikacji w najważniejszych punktach w czasie i zarejestrowane zdarzenia. Debugowanie kodu bez ustawienie wiele punktów przerwania lub ponownego uruchamiania aplikacji jako często. Wymaga programu Visual Studio Enterprise.

[Śledzenie i instrumentacja aplikacji](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)  
W tym artykule opisano, śledzenie, sposób można monitorować wykonywania aplikacji, gdy jest uruchomiona i instrumentacji, która obejmuje umieszczenie instrukcji śledzenia strategicznych lokalizacji w kodzie. Ten temat zawiera również linki do wprowadzenie do Instrumentacji i śledzenia, przełączniki śledzenia, obiekty nasłuchujące śledzenia kodu w aplikacji, Dodawanie instrukcji śledzenia do kodu aplikacji i kompilowanie warunkowe ze śledzenia <xref:System.Diagnostics.Debug> i <xref:System.Diagnostics.Trace> .

[/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute)  
Zawiera opis opcji konsolidatora, która dodaje <xref:System.Diagnostics.DebuggableAttribute> do kod napisany w języku C++. Ten atrybut jest wymagany, aby użyć debugowania funkcji, takich jak dołączanie z C++.

[Debugowanie aplikacji usług systemu Windows](/dotnet/framework/windows-services/how-to-debug-windows-service-applications)  
Zagadnienia dotyczące debugowanie aplikacji usług systemu Windows, w tym konfigurowania, dołączanie do procesu, debugowanie kodu w tej usłudze zawiera `OnStart` metodę i kod w metodzie Main, ustawianie punktów przerwania i za pomocą kontroli usług Menedżer uruchamianie, zatrzymywanie, wstrzymywanie i kontynuować korzystanie z usługi.

[Debugowanie i profilowania](/dotnet/framework/debug-trace-profile/index)  
W tym artykule omówiono debugowanie aplikacji .NET Framework i wymagania dotyczące konfiguracji.

[Debugowanie skryptów i aplikacji sieci Web](../debugger/debugging-web-applications-and-script.md)  
W tym artykule opisano typowe problemy debugowania i techniki, które można napotkać podczas debugowania skryptu i aplikacji sieci Web.

[Nowości w debugerze programu Visual Studio 2015](../debugger/what-s-new-for-the-debugger-in-visual-studio.md)  
Opis nowych funkcji debugowania dodane w tej wersji programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

[Debugowanie strony głównej](../debugger/debugger-feature-tour.md)  
Zawiera łącza do większych sekcji debugowania. Informacje obejmują, co jest nowego w debugerze, ustawienia i przygotowanie, punkty przerwania, obsługa wyjątków, Edytuj i Kontynuuj, debugowanie zarządzanego kodu, debugowanie projektów Visual C++, debugowania COM i ActiveX, debugowanie bibliotek DLL, debugowanie SQL, a użytkownik odwołania do interfejsu.

## <a name="see-also"></a>Zobacz także

[Wskazówki: Debugowanie Windows niestandardowych formantów formularzy w czasie projektowania](/dotnet/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time)
[zabezpieczenia debugera](../debugger/debugger-security.md)
[debugowania w programie Visual Studio](../debugger/index.md) 
 [ Przegląd funkcji debugera](../debugger/debugger-feature-tour.md)