---
title: Projektant przepływu pracy — Projektant działań InvokeMethod
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.InvokeMethod.UI
ms.assetid: 15e6efdc-52ca-46d8-9c5e-063f7c8265a6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 03c62abe30fe2ba3896885d1969a3ec2bc45cc86
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36757769"
---
# <a name="invokemethod-activity-designer"></a>InvokeMethod, projektant działań

**InvokeMethod** Projektant służy do tworzenia i konfigurowania <xref:System.Activities.Statements.InvokeMethod> działania.

## <a name="the-invokemethod-activity"></a>Działanie InvokeMethod

<xref:System.Activities.Statements.InvokeMethod> Wywołuje publiczną metodę określonego obiektu lub typu.

### <a name="use-the-invokemethod-activity-designer"></a>Za pomocą projektanta InvokeMethod działania

Dostęp **InvokeMethod** Projektant działań w **podstawowych** kategorii **przybornika**. **InvokeMethod** Projektant działań mogą być przeciągnięte z **przybornika** i porzucić na powierzchni projektanta przepływów pracy w przypadku gdy zabezpieczając działania są zwykle umieszczane, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Projektant działań porzucenie tworzy <xref:System.Activities.Statements.InvokeMethod> działania z domyślną <xref:System.Activities.Activity.DisplayName%2A> z InvokeMethod. <xref:System.Activities.Activity.DisplayName%2A> Można edytowane w nagłówku **InvokeMethod** Projektant działań lub **DisplayName** pola siatki właściwości.

### <a name="the-invokemethod-properties"></a>Właściwości InvokeMethod

W poniższej tabeli przedstawiono <xref:System.Activities.Statements.InvokeMethod> właściwości i opisano sposób ich używania w projektancie. Te właściwości można edytować w siatce właściwości, a niektóre można edytowane na powierzchni projektanta przepływów pracy.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa <xref:System.Activities.Statements.InvokeMethod> działania. Wartość domyślna to InvokeMethod.<br /><br /> Mimo że <xref:System.Activities.Activity.DisplayName%2A> nie jest ścisłym wymogiem, najlepiej użyć jednego.|
|<xref:System.Activities.Statements.InvokeMethod.MethodName%2A>|True|Nazwa metody do wywołania, gdy działanie wykonuje. Wywołana metoda musi zostać zadeklarowana jako **publicznego**. Ta właściwość może być edytowany na powierzchnię projektanta i jest wymagane.|
|<xref:System.Activities.Statements.InvokeMethod.Parameters%2A>|False|Kolekcja parametrów wywołaną metodę. Parametry należy dodać do kolekcji w tej samej kolejności, w jakiej występują w podpisie metody. Aby wyświetlić **parametry** okna dialogowego, w którym można ustawić tę właściwość, kliknij przycisk wielokropka **parametry** pole siatki właściwości. Kliknij przycisk **utworzyć Argument** przycisk, aby dodać parametry.|
|<xref:System.Activities.Statements.InvokeMethod.Result%2A>|False|Wartość zwracana wywołania metody.|
|<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>|True|Określa, czy metoda jest wywoływana asynchronicznie. Wartość domyślna to **False**.|
|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>|False|Obiekt zawierający metodę do wywołania. Tej właściwości można edytować na powierzchnię projektanta.<br /><br /> Albo <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> lub <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> musi być ustawiona.|
|<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>|False|Typ <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>. Tej właściwości można edytować na powierzchnię projektanta. Ta właściwość musi ustawić, tylko jeśli wywołana metoda jest statyczna.|

Do przekazania parametrów języka C# **limit** parametru (na przykład `Method1(out myParam))`, użyj **OutArgument** zamiast **InOutArgument**

Metody z argumentami o nazwie **TargetObject** lub **wynik** nie można wywołać za pomocą <xref:System.Activities.Statements.InvokeMethod> działania. Jest to spowodowane tym, że <xref:System.Activities.Statements.InvokeMethod> rejestrów działania <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A>, <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> i <xref:System.Activities.Statements.InvokeMethod.Result%2A> w <xref:System.Activities.Activity.CacheMetadata%2A>.

Algorytm rejestrowanie parametrów w <xref:System.Activities.Activity.CacheMetadata%2A> przedstawiono na poniższej liście:

1.  Zarejestruj <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> argumentu.

2.  Zarejestruj <xref:System.Activities.Statements.InvokeMethod.Result%2A> argumentu.

3.  Iterowanie za pomocą <xref:System.Activities.Statements.InvokeMethod.Parameters%2A> kolekcji i zarejestrować każdy argument.

Wynikowa wyjątku jest typu <xref:System.Activities.InvalidWorkflowException> z następującym komunikatem: "InvokeMethod": zmienna, obiekt RuntimeArgument lub DelegateArgument już istnieje o nazwie "TargetObject". Nazwy muszą być unikatowe w zakresie środowiska.

To ograniczenie nie dotyczy <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> i <xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>. Nie ma argumentów przepływu pracy i dlatego nie są zarejestrowane w <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> Kolekcja <xref:System.Activities.Statements.InvokeMethod> działania w <xref:System.Activities.Activity.CacheMetadata%2A> metody.

## <a name="see-also"></a>Zobacz także

- [Typy pierwotne](../workflow-designer/primitives-activity-designers.md)
- [Przypisz](../workflow-designer/assign-activity-designer.md)
- [Opóźnienie](../workflow-designer/delay-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)