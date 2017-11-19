---
title: Debugowanie historyczne | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7cc5ddf2-2f7c-4f83-b7ca-58e92e9bfdd2
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6507ce8544c2dc3bc9085cbcab70a87f04176c17
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2017
---
# <a name="historical-debugging"></a>Debugowanie historyczne
Debugowanie historyczne jest tryb debugowania, która zależy od informacji zbieranych przez IntelliTrace. Umożliwia przechodzenie do tyłu i do przodu do wykonywania aplikacji i sprawdź jej stan.  
  
 Można użyć funkcji IntelliTrace w Visual Studio Enterprise edition (ale nie wersji Professional lub społeczności).  
  
## <a name="why-use-historical-debugging"></a>Dlaczego warto używać debugowania historycznego?  
 Ustawianie punktów przerwania, aby znaleźć błędy może być raczej hit-or-miss affair. Ustaw punkt przerwania zbliża się miejsce w kodzie gdzie podejrzewasz usterki by można następnie uruchom aplikację w debugera i nadzieję, który punkt przerwania pobiera trafień i że miejsce, w którym przerywa wykonywanie może ujawnić źródło błędu. W przeciwnym razie trzeba będzie spróbuj ustawić punkt przerwania gdzieś w kodzie i ponownie uruchom debuger samodzielnego wykonywania kroków testu do momentu znalezienia problemu.  
  
 ![ustawienia punktu przerwania](../debugger/media/breakpointprocesa.png "BreakpointProcesa")  
  
 Można użyć funkcji IntelliTrace i debugowanie historyczne są przekazywane wokół w aplikacji i sprawdź jej stan (stosu wywołań i zmiennych lokalnych) bez konieczności Ustaw punkty przerwania, uruchom ponownie debugowanie i powtórz kroki testu. To może zaoszczędzić dużo czasu, szczególnie gdy usterki znajduje się w scenariuszu testu, który zajmuje dużo czasu na wykonanie.  
  
## <a name="how-do-i-start-using-historical-debugging"></a>Jak rozpocząć debugowania historycznego?  
 Funkcja IntelliTrace jest domyślnie włączone. Wystarczy, że będzie zdecydować, które zdarzenia i wywołania funkcji są przydatne, i określa, czy chcesz wyświetlić migawki z pełnym stanem aplikacji. Aby uzyskać więcej informacji na temat definiowania mają być wyszukiwane, zobacz [funkcji IntelliTrace](../debugger/intellitrace-features.md).  

 - Aby wyświetlić migawki z debugowania historycznego, zobacz [wyświetlić migawki za pomocą kroku zwrotnego IntelliTrace](../debugger/how-to-use-intellitrace-step-back.md)
 - Aby dowiedzieć się, jak sprawdzić zmienne i przejdź do kodu, zobacz [kontroli aplikacji za pomocą debugowania historycznego](../debugger/historical-debugging-inspect-app.md)
 - Aby dowiedzieć się więcej na temat debugowania za pomocą zdarzeń funkcji IntelliTrace, zobacz [wskazówki: przy użyciu funkcji IntelliTrace](../debugger/walkthrough-using-intellitrace.md).