---
title: 'Porady: Konfigurowanie zasad wydajności | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.ruleseditor
ms.assetid: a148b468-b849-4858-880a-808a6b47e596
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bfe6e10c42188cab23c75262d947c7deb9c28ea5
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2018
ms.locfileid: "34816032"
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