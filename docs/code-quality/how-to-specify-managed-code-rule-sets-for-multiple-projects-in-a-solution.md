---
title: "Porady: określanie zestawów reguł zarządzanego kodu dla wielu projektów w rozwiązaniu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.codeanalysis.propertypages.solution
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: e0b6a2864340f87702b765f49605ebdb3aaa555c
ms.sourcegitcommit: bfa26fd7426af0d065cb2eef3d6827b5d6f7986c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2018
---
# <a name="how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution"></a>Porady: określanie zestawów reguł zarządzanego kodu dla wielu projektów w rozwiązaniu

Domyślnie wszystkie projekty zarządzanego rozwiązania są przypisane Microsoft minimalna zalecana reguł analizy kodu *zestaw reguł*. Można zmienić zestawów reguł, które są przypisane do projektów rozwiązania w oknie dialogowym właściwości dla rozwiązania.

> [!NOTE]
> Domyślnie analizy kodu projektu nie jest uruchamiane jako kroku kompilacji. Aby włączyć analizę kodu na potrzeby kompilacji, zobacz [porady: Konfigurowanie analizy kodu dla zarządzanego kodu projektu](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md).

1. Otwórz rozwiązanie w programie Visual Studio.

2. Na **Analizuj** menu, kliknij przycisk **Konfigurowanie analizy kodu dla rozwiązania**.

3. Jeśli to konieczne, rozwiń węzeł **wspólne właściwości**, a następnie kliknij przycisk **ustawienia analizy kodu**.

4. Można określić zestawu reguł dla jednego lub więcej projektów.

    - Aby określić zestaw reguł dla pojedynczego projektu, kliknij nazwę projektu.

    - Aby określić zestawu reguł dla wielu projektów, przytrzymaj klawisz CTRL i kliknij nazwę projektu.

    - Aby określić wszystkie projekty w rozwiązaniu, przytrzymaj naciśnięty klawisz SHIFT, a następnie kliknij pozycję na liście projektu.

5. Kliknij przycisk **zestawu reguł** pole projektu i następnie kliknij polecenie Ustaw nazwę reguły chcesz zastosować.