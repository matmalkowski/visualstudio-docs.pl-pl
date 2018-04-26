---
title: Projektant przepływu pracy — Projektant działań PickBranch
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.PickBranch.UI
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7ea106a96a5d6b81ee0b0b898c881eb752582f8d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="pickbranch-activity-designer"></a>Projektant działań PickBranch

<xref:System.Activities.Statements.PickBranch> Zapewnia oparte na zdarzeniu ścieżkę wykonywania w <xref:System.Activities.Statements.Pick> działanie, które mogą być wyzwalane przez zdarzenia przychodzącego.

## <a name="pickbranch"></a>PickBranch

<xref:System.Activities.Statements.PickBranch> obiekty są zawarte w <xref:System.Activities.Statements.Pick.Branches%2A> Kolekcja <xref:System.Activities.Statements.Pick> działania. Każdy <xref:System.Activities.Statements.PickBranch> znajduje się w gałęzi <xref:System.Activities.Statements.Pick> działania i mogą być wykonywane z powodu niektóre zdarzenia przychodzącego, która służy jako wyzwalacz. W ten sposób projektanta przepływów pracy programu Windows udostępnia modelowanie przepływu sterowania opartego na zdarzeniach. Każdy <xref:System.Activities.Statements.PickBranch> zawiera <xref:System.Activities.Statements.PickBranch.Trigger%2A> i <xref:System.Activities.Statements.PickBranch.Action%2A>.

### <a name="how-to-use-the-pick-activity-designer"></a>Jak używać Projektant działań pobrania

**PickBranch** designer znajduje się w **przepływ sterowania** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika** Karta w Projektancie przepływów pracy (można także wybrać **narzędzi** z **widoku** menu lub CTRL + ALT + X).

Dwa puste <xref:System.Activities.Statements.PickBranch> obiekty o wyświetlić nazwy **Branch1** i **Branch2** jest tworzonych domyślnie jako elementy <xref:System.Activities.Statements.Pick> działania podczas **wybierz** Projektant działań początkowo zostało porzucone do projektanta przepływów pracy. Te odpowiednich <xref:System.Activities.Statements.PickBranch.DisplayName%2A> wartości właściwości mogą być edytowane w **PickBranch** projektanta nagłówka lub poziomu **właściwości** okna dla każdej gałęzi.

Istnieją dwa sposoby dodawania <xref:System.Activities.Statements.PickBranch> obiekty do kolekcji <xref:System.Activities.Statements.Pick> obiektu: przeciąganie i upuszczanie **PickBranch** projektanta z **przybornika** lub korzystając z menu kontekstowego w ramach **wybierz** powierzchni projektu:

1.  **PickBranch** Projektant <xref:System.Activities.Statements.PickBranch> kiedy zostanie przeciągnięty z **przybornika** i upuścić na jednej z gałęzi **wybierz** Projektant działań na Powierzchni projektanta przepływów pracy. Nowy <xref:System.Activities.Statements.PickBranch> obiekty mogą być umieszczony wewnątrz <xref:System.Activities.Statements.Pick> projektanta po lewej lub prawej wszelkie istniejące <xref:System.Activities.Statements.PickBranch> elementy znajdujące się już w kolekcji. Podczas przeciągania **PickBranch** projektanta na **wybierz** projektanta za pomocą myszy **wybierz** projektanta używa pionowy pasek szary blue wskaż, gdzie <xref:System.Activities.Statements.PickBranch> jest dodawany do położenia danej myszy.

2.  Kliknij prawym przyciskiem myszy **wybierz** Projektant działań (, ale nie do wewnątrz **PickBranch** designer) uzyskać menu kontekstowe i wybierz **utwórz gałąź** Aby dodać nowy <xref:System.Activities.Statements.PickBranch>. Zwróć uwagę, że nowe <xref:System.Activities.Statements.PickBranch> jest dodawany do prawej istniejącej <xref:System.Activities.Statements.PickBranch> obiekty w **wybierz** projektanta.

 **PickBranch** projektanta można rozszerzyć, aby ujawnić **wyzwalacza** i **akcji** pola lub zwinięte, klikając podwójne daszka po prawej stronie ich nagłówki. Edytuj <xref:System.Activities.Statements.PickBranch.Trigger%2A> i <xref:System.Activities.Statements.PickBranch.Action%2A> każdego <xref:System.Activities.Statements.PickBranch> upuszczając działań do **wyzwalacza** i **akcji** pola ich projektantów.

 <xref:System.Activities.Statements.PickBranch> Obiekty w <xref:System.Activities.Statements.Pick.Branches%2A> Kolekcja <xref:System.Activities.Statements.Pick> obiektów, można zmienić kolejności przez przeciąganie i upuszczanie je do nowej lokalizacji w ramach **wybierz** projektanta. **Wybierz** projektanta używa pionowy pasek szary blue wskaż, gdzie <xref:System.Activities.Statements.PickBranch> jest dodawany do umieszczenia danego myszy.

 Istnieją dwa sposoby, aby usunąć <xref:System.Activities.Statements.PickBranch>:

1.  Wybierz **PickBranch** projektanta i usuń go.

2.  Wybierz **PickBranch** projektanta, kliknij prawym przyciskiem myszy uzyskać menu kontekstowe i wybierz **usunąć**.

 Należy wybrać **PickBranch** projektanta, jak wybrać jedną z działań wewnątrz jego **wyzwalacza** lub **akcji** pola przez pomyłkę usuwa jeden z tych działań i nie <xref:System.Activities.Statements.PickBranch> obiektu.

### <a name="pickbranch-properties-in-the-workflow-designer"></a>Właściwości PickBranch w Projektancie przepływów pracy
 W poniższej tabeli przedstawiono najbardziej przydatne <xref:System.Activities.Statements.PickBranch> właściwości oraz opis sposobu ich używania w Projektancie przepływów pracy.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|False|Przyjazna nazwa wyświetlana w nagłówku **PickBranch** projektanta. Wartość domyślna to gałęzi.<br /><br /> Mimo że <xref:System.Activities.Activity.DisplayName%2A> nie jest ścisłym wymogiem jest najlepszym rozwiązaniem jej użyć.|
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|True|Każdy <xref:System.Activities.Statements.PickBranch> zawiera <xref:System.Activities.Statements.PickBranch.Trigger%2A> akcji, które może wywołać <xref:System.Activities.Statements.PickBranch.Action%2A>.|
|<xref:System.Activities.Statements.PickBranch.Action%2A>|False|Każdy <xref:System.Activities.Statements.PickBranch> zawiera <xref:System.Activities.Statements.PickBranch.Action%2A> wykonaniu Jeśli wyzwolone.|

## <a name="see-also"></a>Zobacz także

- [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)
- [Wybieranie działania](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [Używanie działania Pick](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)