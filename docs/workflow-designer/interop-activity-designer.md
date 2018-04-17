---
title: Projektant działań międzyoperacyjnego | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bbac122e2e12844249be8dad37d6bed65b90ddc3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="interop-activity-designer"></a>Projektant działania Interop
**Międzyoperacyjności** Projektant działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.Interop> działania.

## <a name="the-interop-activity"></a>Działania Interop
 <xref:System.Activities.Statements.Interop> Działanie zarządza wykonywania typów wyprowadzonych z <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> w przepływie pracy.

### <a name="using-the-interop-activity-designer"></a>Przy użyciu narzędzia Projektant działania Interop
 **Międzyoperacyjności** Projektant działań można znaleźć w **migracji** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika**kartę (można także wybrać **przybornika** z **widoku** menu lub CTRL + ALT + X.)

 [Migracji](../workflow-designer/migration-activity-designers.md) kategorię, która zawiera <xref:System.Activities.Statements.Interop> działania tylko zostaną wyświetlone w **przybornika** Jeśli Twój projekt jest docelowo pełnego [!INCLUDE[netfx40_long](../workflow-designer/includes/netfx40_long_md.md)].

 Dla projektów C#, można kierować ponownie projekt do używania w pełni [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] przez kliknięcie prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierając **właściwości**. Na **aplikacji** wybierz opcję **NET Framework 4** opcji **platformy docelowej**. Wybierz **tak** przycisk **docelowej Framework zmienić** okno dialogowe wyświetla z prośbą o potwierdzenie tej zmiany.

 Dla projektów języka VB, można kierować ponownie projekt do używania w pełni [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] przez kliknięcie prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierając **właściwości**. Na **skompilować** , kliknij pozycję **zaawansowane opcje kompilacji** przycisku. Wybierz **.Net Framework 4** z **listy docelowej framework** , a następnie kliknij przycisk **OK**. Kliknij przycisk **tak** przycisk **docelowej Framework zmienić** okno dialogowe wyświetla z prośbą o potwierdzenie tej zmiany.

 **Międzyoperacyjności** Projektant działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] powierzchni we wszystkich działań zwykle są umieszczane, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie <xref:System.Activities.Statements.Interop> działania z domyślną **DisplayName** z Interop. <xref:System.Activities.Activity.DisplayName%2A> Można edytowane w nagłówku **międzyoperacyjności** Projektant działań lub **DisplayName** pola siatki właściwości.

 Kliknij przycisk **kliknij, aby przeglądać...**  tekst w **ActivityType** okno, albo na **międzyoperacyjności** działania projektanta lub w siatce właściwości, aby wyświetlić **Przeglądaj i wybierz .net typ** okno dialogowe. Tylko typy dla przepływu pracy 3.0 lub 3.5 przepływu pracy działania (to znaczy tylko typy pochodzące z <xref:System.Workflow.ComponentModel.Activity>). Aby uzyskać więcej informacji na temat przy użyciu tego pola, aby określić typ, zobacz [Wyszukaj i wybierz typ .NET dialogowe](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md) tematu.

### <a name="the-interop-properties"></a>Właściwości międzyoperacyjne
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.Interop> właściwości oraz opis korzystania z nich w projektancie. Te właściwości można edytować w siatce właściwości lub na [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] powierzchni.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa <xref:System.Activities.Statements.Interop> działania. Wartość domyślna to Interop. Wyświetlana nazwa nie jest ściśle wymagane, jest najlepszym rozwiązaniem, aby użyć nazwy wyświetlanej.|
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|True|Określa typ działania zawarty w <xref:System.Activities.Statements.Interop> działania. Ten określony typ musi pochodzić od <xref:System.Workflow.ComponentModel.Activity>.|

## <a name="see-also"></a>Zobacz także

- [Migracja](../workflow-designer/migration-activity-designers.md)