---
title: Projektant przepływu pracy — Projektant działania TryCatch
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.TryCatch.UI
- System.Activities.Statements.Catch`1.UI
ms.assetid: 02a326c2-4009-442f-b7cb-e42121fd2992
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 26985893ae5a6431743564e28793957ecf0f9e01
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756817"
---
# <a name="trycatch-activity-designer"></a>TryCatch, projektant działań

**TryCatch** Projektant działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.TryCatch> działania.

## <a name="the-trycatch-activity"></a>Działanie TryCatch
 <xref:System.Activities.Statements.TryCatch> Zawiera działanie <xref:System.Activities.Statements.TryCatch.Try%2A> działanie, Kolekcja **Catch\<TException >** i <xref:System.Activities.Statements.TryCatch.Finally%2A> działania. A <xref:System.Activities.Statements.Catch%601> typu **TException** zawiera <xref:System.Activities.Statements.Catch%601.ExceptionType%2A> i <xref:System.Activities.Statements.Catch%601.Action%2A>. Razem są one używane do zaimplementowania typowych błędów na podstawie wyjątek mechanizmu obsługi. A <xref:System.Activities.Statements.TryCatch> działania próbuje wykonać jego <xref:System.Activities.Statements.TryCatch.Try%2A> działania. Jeśli <xref:System.Activities.Statements.TryCatch.Try%2A> działania zgłoszenie wyjątku, <xref:System.Activities.Statements.TryCatch> działania używa jej **Catch < TException\>**  kolekcji, aby dopasować wyjątek. Jeśli istnieje dopasowanie, a następnie <xref:System.Activities.Statements.Catch%601.Action%2A> odpowiadającego **Catch\<TException >** jest wykonywane, służąc jako błąd obsługi logiki dla wyjątku. Jeśli działania w <xref:System.Activities.Statements.TryCatch.Try%2A> sekcji zostało ukończone pomyślnie, lub działania w <xref:System.Activities.Statements.TryCatch.Catches%2A> zostało ukończone pomyślnie, <xref:System.Activities.Statements.TryCatch> wykonuje działania jego <xref:System.Activities.Statements.TryCatch.Finally%2A> działania. Aby uzyskać więcej informacji, zobacz [wyjątki przepływu pracy systemu Windows](/dotnet/framework/windows-workflow-foundation/exceptions).

### <a name="using-the-trycatch-activity-designer"></a>Przy użyciu narzędzia Projektant działania TryCatch

Dostęp **TryCatch** Projektant działań w **obsługi błędu** kategorii **przybornika**.

**TryCatch** Projektant działań mogą być przeciągnięte z **przybornika** i porzucić na powierzchni projektanta przepływów pracy wszędzie tam, gdzie działania są zwykle umieszczane, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie <xref:System.Activities.Statements.TryCatch> działania z domyślną <xref:System.Activities.Activity.DisplayName%2A> z TryCatch. <xref:System.Activities.Activity.DisplayName%2A> Wartość można edytować w nagłówku **TryCatch** Projektant działań lub **DisplayName** pola siatki właściwości. Inne właściwości, należy edytować na powierzchni **TryCatch** Projektant działań.

Kliknij przycisk rozwijania w prawym górnym rogu **TryCatch** projektanta, aby wyświetlić **spróbuj**, **przechwytuje**, i **koniec** pól widoku rozszerzonego. Aby dodać catch, kliknij przycisk **Dodaj nowe catch** znajdującego się na **TryCatch** projektanta. Przycisk zostanie zmieniony na typ pola kombi. Wybierz typ wyjątku, a następnie naciśnij klawisz ENTER, aby dodać catch. Po dodaniu **Catch**, obszar catch rozszerza i działania można było porzucić do catch do definiowania logiki wykonywania dla catch. Należy pamiętać, że pole tekstowe po prawej stronie obszaru rozwinięte catch. Można określić nazwę zmiennej wyjątek przy użyciu tego pola tekstowego. Zmienna wyjątku jest możliwe tylko dla działań w tym samym **Catch**.

**TryCatch** Projektant nie obsługuje edycji **Catch**. Jeśli chcesz zmienić typ wyjątku, musisz usunąć **Catch** i dodania nowego. A **Catch** można usunąć, wybierając ją i usunięcie go lub za pomocą **usunąć** menu dostępnego po kliknięciu prawym przyciskiem myszy menu kontekstowego.

### <a name="the-trycatch-properties"></a>Właściwości TryCatch

W poniższej tabeli przedstawiono <xref:System.Activities.Statements.TryCatch>właściwości oraz opis korzystania z nich w projektancie.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Określa opcjonalne przyjazna nazwa <xref:System.Activities.Statements.TryCatch> działania. Wartość domyślna to TryCatch.|
|<xref:System.Activities.Statements.TryCatch.Try%2A>|False|Gdy wykonywany jako pierwszy działania <xref:System.Activities.Statements.TryCatch> wykonuje.|
|<xref:System.Activities.Statements.TryCatch.Catches%2A>|False|Kolekcja **Catch** elementy do wyewidencjonowania po <xref:System.Activities.Statements.TryCatch.Try%2A> działania zgłasza wyjątek.<br /><br /> Jedno działanie w co najmniej należy dodać <xref:System.Activities.Statements.TryCatch.Catches%2A> lub działania w <xref:System.Activities.Statements.TryCatch.Finally%2A> bloku.|
|<xref:System.Activities.Statements.TryCatch.Finally%2A>|False|Działanie do wykonania po <xref:System.Activities.Statements.TryCatch.Try%2A> oraz wszelkie niezbędne działania w <xref:System.Activities.Statements.TryCatch.Catches%2A> ukończenie kolekcji.<br /><br /> Jedno działanie w co najmniej należy dodać <xref:System.Activities.Statements.TryCatch.Catches%2A> lub działania w <xref:System.Activities.Statements.TryCatch.Finally%2A> bloku.|

## <a name="see-also"></a>Zobacz także

- [Kolekcja](../workflow-designer/collection-activity-designers.md)
- [rethrow](../workflow-designer/rethrow-activity-designer.md)
- [Throw](../workflow-designer/throw-activity-designer.md)