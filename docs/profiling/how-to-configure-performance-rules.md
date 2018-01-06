---
title: "Porady: Konfigurowanie zasad wydajności | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.performance.ruleseditor
ms.assetid: a148b468-b849-4858-880a-808a6b47e596
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c9b389f570a1dd0a16fb4266268be953433aaa1e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-performance-rules"></a>Porady: Konfigurowanie zasad wydajności
Ostrzeżenia wydajności o tym Visual Studio Profiling Tools wskazują na problemy w profilowanych aplikacji, która może spowolnić działanie programu. Ostrzeżenia może również oznaczać, że może być konieczna zmiana metody kolekcji do zbierania danych bardziej użyteczne. Ostrzeżenia wydajności są generowane automatycznie podczas sesji profilowania i są wyświetlane w **listy błędów** okna po otwarciu pliku danych profilowania w [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. Określone ostrzeżenia nie mogą być stosowane do scenariuszy planuje się, czy ostrzeżenia może zostać wywołane nieprawidłowo. Można skonfigurować ostrzeżeń dotyczących wydajności, aby pokazać lub ukryć określone ostrzeżenia.  
  
### <a name="to-configure-profiler-performance-warnings"></a>Aby skonfigurować ostrzeżeń dotyczących wydajności programu profilującego  
  
1.  Na **narzędzia** menu, kliknij przycisk **opcje**.  
  
2.  Rozwiń węzeł **narzędzi wydajności**, a następnie kliknij przycisk **reguły**.  
  
3.  Aby włączyć lub wyłączyć ostrzeżenie, zaznacz lub wyczyść pole wyboru obok ostrzeżenia **identyfikator** i nazwę.  
  
4.  Aby określić poziom warring regułę, kliknij przycisk **akcji** komórki obok reguły, a następnie kliknij przycisk poziom ostrzeżeń.  
  
    -   **Wyłączone** — wyłącza regułę (jest to taka sama jak usuwając zaznaczenie pola wyboru obok identyfikator reguły).  
  
    -   **Ostrzeżenie** -Wyświetla reguły jako ostrzeżenia.  
  
    -   **Błąd** — zatrzymuje profilowanie wykonywania i wyświetla reguł jako błąd.  
  
    -   **Informacje o** -Wyświetla reguły jako tylko informacje.