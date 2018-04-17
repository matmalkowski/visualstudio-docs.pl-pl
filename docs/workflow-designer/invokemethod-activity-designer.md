---
title: Projektant działań InvokeMethod | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.InvokeMethod.UI
ms.assetid: 15e6efdc-52ca-46d8-9c5e-063f7c8265a6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fe2e1cbb097d86d0e13ba8581389d7356001ff92
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="invokemethod-activity-designer"></a>Projektant działań InvokeMethod
**InvokeMethod** Projektant służy do tworzenia i konfigurowania <xref:System.Activities.Statements.InvokeMethod> działania.

## <a name="the-invokemethod-activity"></a>Działanie InvokeMethod
 <xref:System.Activities.Statements.InvokeMethod> Wywołuje publiczną metodę określonego obiektu lub typu.

### <a name="using-the-invokemethod-activity-designer"></a>Przy użyciu narzędzia Projektant działań InvokeMethod
 **InvokeMethod** Projektant działań można znaleźć w **podstawowych** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika** kartę [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (można także wybrać **narzędzi** z **widoku** menu lub klawiszy CTRL + ALT + X.)

 **InvokeMethod** Projektant działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] powierzchni gdziekolwiek działań zwykle są umieszczane, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie <xref:System.Activities.Statements.InvokeMethod> działania z domyślną <xref:System.Activities.Activity.DisplayName%2A> z InvokeMethod. <xref:System.Activities.Activity.DisplayName%2A> Można edytowane w nagłówku **InvokeMethod** Projektant działań lub **DisplayName** pola siatki właściwości.

### <a name="the-invokemethod-properties"></a>Właściwości InvokeMethod
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.InvokeMethod> właściwości oraz opis korzystania z nich w projektancie. Te właściwości można edytować w siatce właściwości i niektóre mogą być edytowane [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]powierzchnię projektanta.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa <xref:System.Activities.Statements.InvokeMethod> działania. Wartość domyślna to InvokeMethod.<br /><br /> Mimo że <xref:System.Activities.Activity.DisplayName%2A> nie jest ścisłym wymogiem jest najlepszym rozwiązaniem jej użyć.|
|<xref:System.Activities.Statements.InvokeMethod.MethodName%2A>|True|Nazwa metody do wywołania, gdy działanie wykonuje. Wywołana metoda musi zostać zadeklarowana jako **publicznego**. Tej właściwości można edytować na powierzchnię projektanta. Jest to wymagane właściwości.|
|<xref:System.Activities.Statements.InvokeMethod.Parameters%2A>|False|Kolekcja parametrów wywołaną metodę. Parametry należy dodać do kolekcji w tej samej kolejności, w jakiej występują w podpisie metody. Siatki właściwości, kliknij przycisk wielokropka w **parametry** pola, wyświetla **parametry** okna dialogowego, aby można było ustawić tę właściwość. Kliknij przycisk **utworzyć Argument** przycisk, aby dodać parametry.|
|<xref:System.Activities.Statements.InvokeMethod.Result%2A>|False|Wartość zwracana wywołania metody.|
|<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>|True|Określa, czy metoda jest wywoływana asynchronicznie. Wartość domyślna to **False**.|
|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>|False|Obiekt zawierający metodę do wywołania. Tej właściwości można edytować na powierzchnię projektanta.<br /><br /> Albo <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> lub <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> musi być ustawiona.|
|<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>|False|Typ <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>. Tej właściwości można edytować na powierzchnię projektanta. Ta właściwość musi ustawić, tylko jeśli wywołana metoda jest statyczna.|

 Do przekazania parametrów języka C# **limit** parametru (na przykład `Method1(out myParam)),` należy używać **OutArgument** zamiast **InOutArgument**

 Metody z argumentami o nazwie **TargetObject** lub **wynik** nie można wywołać za pomocą <xref:System.Activities.Statements.InvokeMethod> działania. Jest to spowodowane tym, że <xref:System.Activities.Statements.InvokeMethod> rejestrów działania <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A>, <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> i <xref:System.Activities.Statements.InvokeMethod.Result%2A> w <xref:System.Activities.Activity.CacheMetadata%2A>.

 Algorytm rejestrowanie parametrów w <xref:System.Activities.Activity.CacheMetadata%2A> przedstawiono na poniższej liście:

1.  Zarejestruj <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> argumentu.

2.  Zarejestruj <xref:System.Activities.Statements.InvokeMethod.Result%2A> argumentu.

3.  Iterowanie za pomocą <xref:System.Activities.Statements.InvokeMethod.Parameters%2A> kolekcji i zarejestrować każdy argument.

 Wynikowa wyjątku jest typu <xref:System.Activities.InvalidWorkflowException> z następującym komunikatem: "InvokeMethod": zmienna, obiekt RuntimeArgument lub DelegateArgument już istnieje o nazwie "TargetObject". Nazwy muszą być unikatowe w zakresie środowiska.

 To ograniczenie nie ma zastosowania do <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> i <xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A> , ponieważ nie są argumenty przepływu pracy i dlatego nie są zarejestrowane w <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> Kolekcja <xref:System.Activities.Statements.InvokeMethod> działania w <xref:System.Activities.Activity.CacheMetadata%2A> metody.

## <a name="see-also"></a>Zobacz także

- [Typy pierwotne](../workflow-designer/primitives-activity-designers.md)
- [Przypisz](../workflow-designer/assign-activity-designer.md)
- [Opóźnienie](../workflow-designer/delay-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)