---
title: 'Porady: włączanie i wyłączanie automatycznej analizy kodu dla zarządzanego kodu'
ms.date: 09/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 3113143b07ccb6f765cd0cf1735b34be6e952c72
ms.sourcegitcommit: 6672a1e9d135d7e5cca3cceea07c6fe5a0871475
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47443548"
---
# <a name="how-to-enable-and-disable-automatic-code-analysis-for-managed-code"></a>Porady: Włączanie i wyłączanie automatycznej analizy kodu dla kodu zarządzanego

Można skonfigurować analizy kodu, aby uruchomić po każdej kompilacji projektu kodu zarządzanego. Można ustawić właściwości analizy dla każdej konfiguracji kompilacji inny kod, na przykład debug i release.

## <a name="to-enable-or-disable-automatic-code-analysis"></a>Włączanie lub wyłączanie automatycznej analizy kodu

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **właściwości**.

1. W oknie dialogowym właściwości projektu wybierz **analizy kodu** kartę.

1. Określ typ kompilacji w **konfiguracji** i platformy docelowej w **platformy**.

1. Aby włączyć lub wyłączyć automatycznej analizy kodu, zaznacz lub wyczyść **Włącz analizę kodu podczas kompilacji** pole wyboru.

> [!NOTE]
> **Włącz analizę kodu podczas kompilacji** pole wyboru ma wpływ tylko na statycznej analizy kodu. Nie wpływa na [analizatorów kodu Roslyn](roslyn-analyzers-overview.md), która zawsze wykonać na konferencji build, jeśli został zainstalowany jako pakiet NuGet. Jeśli chcesz wyczyścić błędy analizatora z **lista błędów**, można pominąć wszystkie bieżące naruszenia, wybierając **analizy** > **Uruchom analizę kodu i Pomiń aktywne Problemy z** na pasku menu. Aby uzyskać więcej informacji, zobacz [Pomiń naruszenia](use-roslyn-analyzers.md#suppress-violations).
