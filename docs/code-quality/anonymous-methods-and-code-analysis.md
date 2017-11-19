---
title: Metody anonimowe i analiza kodu | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- methods, anonymous
- code analysis, anonymous methods
- anonymous methods, code analysis
ms.assetid: bf0a1a9b-b954-4d46-9c0b-cee65330ad00
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8ebf550ca92cbefbed684e2b11e0b20b62661133
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="anonymous-methods-and-code-analysis"></a>Metody anonimowe i analiza kodu
*Metody anonimowej* to metoda, która nie ma nazwy. Metody anonimowe są najczęściej używane do przekazania blok kodu jako parametru delegowanego.  
  
 W tym temacie wyjaśniono, jak kod — analiza obsługuje ostrzeżenia i metryk, które są skojarzone z metod anonimowych.  
  
## <a name="anonymous-methods-declared-in-a-member"></a>Metody anonimowe zadeklarowany w elemencie członkowskim  
 Ostrzeżenia i metryki dla metody anonimowej, która jest zadeklarowana w elemencie członkowskim, takich jak metody lub metody dostępu są skojarzone z elementem członkowskim, który deklaruje metody. Nie są one powiązane z elementem członkowskim, który wywołuje metodę.  
  
 Na przykład w następującej klasy wszelkie ostrzeżenia, które znajdują się w deklaracji **anonymousMethod** powinien być wywoływany przed **metoda1** i nie **metoda2**.  
  
```vb  
  
      Delegate Function ADelegate(ByVal value As Integer) As Boolean  
Class AClass  
  
    Sub Method1()  
        Dim anonymousMethod As ADelegate = Function(ByVal value As Integer) value > 5  
        Method2(anonymousMethod)  
    End SubSub Method2(ByVal anonymousMethod As ADelegate)  
        anonymousMethod(10)  
    End SubEnd Class  
```  
  
```csharp  
  
      delegate void Delegate();  
class Class  
{  
    void Method1()  
    {  
        Delegate anonymousMethod = delegate()   
        {   
          Console.WriteLine("");   
        }  
        Method2(anonymousMethod);  
    }  
  
    void Method2(Delegate anonymousMethod)  
    {  
        anonymousMethod();  
    }  
}  
```  
  
## <a name="inline-anonymous-methods"></a>Metody anonimowe wbudowany  
 Ostrzeżenia i metryki dla metody anonimowej jest zadeklarowany jako wbudowany przypisania do pola są skojarzone z konstruktora. Jeśli pole jest zadeklarowany jako `static` (`Shared` w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]), ostrzeżenia i metryki są skojarzone z konstruktora klasy; w przeciwnym razie, są one powiązane z konstruktora wystąpienia.  
  
 Na przykład w następującej klasy wszelkie ostrzeżenia, które znajdują się w deklaracji **anonymousMethod1** zostanie wygenerowany przed niejawnie wygenerowany domyślny konstruktor obiektu **klasy**. Natomiast, które zostały wykryte w **anonymousMethod2** zostaną zastosowane względem konstruktora klasy niejawnie wygenerowany.  
  
```vb  
  
  Delegate Function ADelegate(ByVal value As Integer) As BooleanClass AClass  
Dim anonymousMethod1 As ADelegate = Function(ByVal value As    Integer) value > 5  
Shared anonymousMethod2 As ADelegate = Function(ByVal value As     Integer) value > 5  
  
Sub Method1()  
    anonymousMethod1(10)  
    anonymousMethod2(10)  
End SubEnd Class  
```  
  
```csharp  
  
      delegate void Delegate();  
class Class  
{  
    Delegate anonymousMethod1 = delegate()   
    {   
       Console.WriteLine("");   
    }  
  
    static Delegate anonymousMethod2 = delegate()   
    {   
       Console.WriteLine("");   
    }  
  
    void Method()  
    {  
       anonymousMethod1();  
       anonymousMethod2();  
    }  
}  
```  
  
 Klasy mogą zawierać wbudowanego metody anonimowej, która przypisuje wartość do pola, które zawiera wiele konstruktorów. W takim przypadku ostrzeżenia i metryki są skojarzone z wszystkie konstruktory chyba, że ten konstruktor jest dołączony do innego konstruktora w tej samej klasy.  
  
 Na przykład w następującej klasy wszelkie ostrzeżenia, które znajdują się w deklaracji **anonymousMethod** powinien być wywoływany przed **Class(int)** i **Class(string)** , ale nie przed **Class()**.  
  
```vb  
  
  Delegate Function ADelegate(ByVal value As Integer) As BooleanClass AClass  
  
Dim anonymousMethod As ADelegate = Function(ByVal value As Integer)   
value > 5  
  
SubNew()  
    New(CStr(Nothing))  
End SubSub New(ByVal a As Integer)  
End SubSub New(ByVal a As String)  
End SubEnd Class  
```  
  
```csharp  
  
      delegate void Delegate();  
class Class  
{  
    Delegate anonymousMethod = delegate()   
    {   
       Console.WriteLine("");   
    }  
  
    Class() : this((string)null)  
    {  
    }  
  
    Class(int a)  
    {  
    }  
  
    Class(string a)  
    {  
    }  
}  
```  
  
 Chociaż to rozwiązanie może wydawać się nieoczekiwane, dzieje się tak dlatego kompilator generuje metodę unikatowy dla każdego Konstruktor, który nie będzie powiązany innego konstruktora. Ze względu na to zachowanie naruszenia to miejsce w **anonymousMethod** można pominąć oddzielnie. To również oznacza, że w przypadku nowego Konstruktora wprowadzone, ostrzeżeń, które wcześniej zostały pominięte przed **Class(int)** i **Class(string)** musi również zostać pominięta dla nowego konstruktora.  
  
 Można obejść ten problem w jednym z dwóch sposobów. Można zadeklarować **anonymousMethod** w Konstruktorze wspólnej który wszystkie konstruktory łańcucha. Lub można ją zadeklarować w metodę inicjalizacji, która jest wywoływana przez wszystkie konstruktory.  
  
## <a name="see-also"></a>Zobacz też  
 [Analiza jakości zarządzanego kodu](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)