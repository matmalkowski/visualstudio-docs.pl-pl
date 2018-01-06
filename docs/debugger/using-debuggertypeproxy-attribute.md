---
title: Korzystanie z atrybutu DebuggerTypeProxy | Dokumentacja firmy Microsoft
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
- attributes [C#], debugger
- DebuggerTypeProxyAttribute class
- DebuggerTypeProxy attribute
ms.assetid: 943f3bb1-993e-4800-a47e-0af78b063014
caps.latest.revision: "24"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 36e80508ce0febc7678585faf6518bf6b838a289
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="using-debuggertypeproxy-attribute"></a>Korzystanie z atrybutu DebuggerTypeProxy
<xref:System.Diagnostics.DebuggerTypeProxyAttribute>Określa serwer proxy lub podstawiony typu i zmiany sposobu typ jest wyświetlana w oknach debugera. Po wyświetleniu zmiennej, która jest serwer proxy serwera proxy oznacza oryginalnego typu w **wyświetlić**. Okno zmiennych debugera zawiera tylko publiczne elementy członkowskie typu serwera proxy. Prywatne elementy członkowskie nie są wyświetlane.  
  
 Ten atrybut można stosować do:  
  
-   Struktury  
  
-   Klasy  
  
-   Zestawy  
  
 Typ klasy serwera proxy musi mieć konstruktora, który przyjmuje argument typu, który zastąpi serwera proxy. Debuger tworzy nowe wystąpienie klasy typu serwera proxy za każdym razem, należy go wyświetlić zmiennej typu docelowego. Może to mieć wpływ na wydajność. W związku z tym nie należy przeprowadzać więcej pracy w Konstruktorze niż jest to bezwzględnie konieczne.  
  
 Aby zminimalizować spadku wydajności, Ewaluator wyrażeń nie zbadać atrybutów na serwerze proxy wyświetlania typu chyba, że typ jest rozwinięty, klikając użytkownika symbol w oknie debugera lub przy użyciu + <xref:System.Diagnostics.DebuggerBrowsableAttribute>. W związku z tym nie należy umieścić atrybutów w typie ekranu, sama. Atrybuty można i należy jej używać w treści typu wyświetlania.  
  
 Jest dobrym rozwiązaniem dla obiektu pośredniczącego typu jako prywatnych klasa zagnieżdżona w klasie który docelowe atrybuty. Dzięki temu można łatwo dostęp do wewnętrznych elementów członkowskich.  
  
 Jeśli <xref:System.Diagnostics.DebuggerTypeProxyAttribute> jest używany na poziomie zestawu `Target` parametr określa typ, który zastąpi serwera proxy.  
  
 Na przykład można użyć tego atrybutu wraz z <xref:System.Diagnostics.DebuggerDisplayAttribute> i <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, zobacz[za pomocą atrybutu DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md).  
  
## <a name="using-generics-with-debuggertypeproxy"></a>Użycie typów ogólnych z DebuggerTypeProxy  
 Obsługa ogólne jest ograniczona. Język C# `DebuggerTypeProxy` obsługuje tylko otwarte typów. Typem otwartym, nazywane również unconstructed typ jest typem ogólnym, która nie została utworzona z argumentami jego parametrów typu. Zamknięte typy, nazywane również typy utworzone, nie są obsługiwane.  
  
 Składnia typu otwartego wygląda następująco:  
  
 `Namespace.TypeName<,>`  
  
 Jeśli używasz typem ogólnym jako cel w `DebuggerTypeProxy`, należy użyć następującej składni. `DebuggerTypeProxy` Mechanizmu wnioskuje parametrów typu dla Ciebie.  
  
 Więcej informacji o typach otwarte i zamknięte w języku C# [specyfikacji języka C#](/dotnet/csharp/language-reference/language-specification), otwórz sekcję 20.5.2 i zamknięte typów.  
  
 Visual Basic nie ma typu otwartego składni, tak samo w języku Visual Basic nie można wykonywać. Zamiast tego należy użyć nazwy typu otwartego reprezentację ciągu.  
  
 `"Namespace.TypeName'2"`  
  
## <a name="see-also"></a>Zobacz też  
 [Za pomocą atrybutu DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)   
 [Tworzenie niestandardowych widoków obiektów .managed](../debugger/create-custom-views-of-dot-managed-objects.md)   
 [Udoskonalanie debugowania za pomocą atrybutów wyświetlania debugera](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)