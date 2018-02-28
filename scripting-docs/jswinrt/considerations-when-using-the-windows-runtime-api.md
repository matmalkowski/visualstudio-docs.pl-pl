---
title: "Uwagi dotyczące korzystania z interfejsu API środowiska wykonawczego systemu Windows | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JavaScript, Windows Runtime API
ms.assetid: 2f56d70c-c80d-4876-8e6a-8ae031d31c22
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 693b3dac9def5533417638c3ec1c0de8db1d5fe3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="considerations-when-using-the-windows-runtime-api"></a>Uwagi dotyczące korzystania z interfejsu API środowiska wykonawczego systemu Windows
Można użyć niemal każdego elementu interfejsu API środowiska wykonawczego systemu Windows w języku JavaScript. Istnieją jednak niektóre aspekty JavaScript reprezentację elementów środowiska wykonawczego systemu Windows, które należy mieć na uwadze.  
  
> [!IMPORTANT]
>  Aby uzyskać informacje dotyczące tworzenia składników środowiska wykonawczego systemu Windows w języku C++, C# lub Visual Basic i korzystanie z nich w języku JavaScript, zobacz [tworzenia składników środowiska wykonawczego systemu Windows w języku C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp) i [tworzenia składników środowiska wykonawczego systemu Windows w języku C# i Visual Basic](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic).  
  
## <a name="special-cases-in-the-javascript-representation-of-windows-runtime-types"></a>Szczególnych przypadkach w JavaScript reprezentację typów środowiska wykonawczego systemu Windows  
  
-   Ciągi: Niezainicjowanej ciąg jest przekazywany jako ciąg "undefined", a ciąg ustawioną do środowiska wykonawczego systemu Windows metody `null` jest przekazywany jako ciąg "null". (Dotyczy to zawsze, gdy `null` lub `undefined` wartość jest traktowany jako ciąg.) Przed ciąg są przekazywane do metody środowiska uruchomieniowego systemu Windows, należy zainicjować go jako ciąg pusty ("").  
  
-   Interfejsy: Nie można zaimplementować interfejsu środowiska wykonawczego systemu Windows w języku JavaScript.  
  
-   Tablice: Tablice środowiska wykonawczego systemu Windows nie są o zmiennym rozmiarze, więc metody, których rozmiar tablic w języku JavaScript nie działają w tablicach środowiska wykonawczego systemu Windows.  
  
-   Tablice: W przypadku przekazania wartości tablicy JavaScript do środowiska wykonawczego systemu Windows metody, tablica jest kopiowana. Metoda środowiska uruchomieniowego systemu Windows nie będzie mógł zmodyfikować tablicy lub jego elementów członkowskich i przywrócić go do aplikacji JavaScript. Można jednak użyć wpisane tablice (na przykład [int32array — obiekt](../javascript/reference/int32array-object.md)), które nie są kopiowane.  
  
-   Struktury: Struktury środowiska wykonawczego systemu Windows są obiekty w języku JavaScript. Jeśli chcesz przekazać strukturę środowiska wykonawczego systemu Windows metody środowiska uruchomieniowego systemu Windows nie tworzenia wystąpienia struktury z `new` — słowo kluczowe. Zamiast tego należy utworzyć obiekt i dodaj odpowiednie elementy członkowskie i ich wartości. Nazwy elementów członkowskich należy w camelcase: `SomeStruct.firstMember`.  
  
-   Obiekty: Obiektów JavaScript nie są takie same obiekty kod zarządzany (`System.Object`). Nie można przekazywać obiektów JavaScript do środowiska wykonawczego systemu Windows metody, która wymaga `System.Object`.  
  
-   Tożsamości obiektów: W większości przypadków obiekty i z powrotem przekazywane między środowiska wykonawczego systemu Windows i JavaScript nie należy zmieniać. Aparat JavaScript przechowuje mapy znanymi obiektami. Gdy obiekt jest zwracany z środowiska uruchomieniowego systemu Windows jest dopasowywana do mapy, a jeśli nie istnieje nowy obiekt zostanie utworzony. Tę samą procedurę nastąpią dla obiektów, które reprezentują interfejsów, które są zwracane przez środowisko wykonawcze systemu Windows metody. Istnieją dwa rodzaje wyjątków:  
  
    -   Obiekty, które są zwracane z Windows Runtime wywołać i wybrać nowe właściwości (expando) dodany, nie zachowuje ich nowych właściwości, gdy są one przekazywane z powrotem do środowiska wykonawczego systemu Windows. Jednak gdy są zwracane do aplikacji JavaScript, ponieważ są one dopasowany do istniejącego obiektu, zwrócony obiekt ma właściwości expando.  
  
    -   Struktury i delegatów w środowiska wykonawczego systemu Windows nie może zostać zidentyfikowana jako taka sama jak używane wcześniej struktury lub delegatów. Za każdym razem, gdy struktury lub delegat jest zwracany, pobiera nowe odwołanie.  
  
-   Nazwa kolizji: interfejsy wielu środowiska wykonawczego systemu Windows mogą mieć elementy członkowskie o tych samych nazwach. Jeśli są one łączone w pojedynczy obiekt JavaScript (która może być reprezentacja klasy środowiska uruchomieniowego lub interfejs), elementy członkowskie są reprezentowane z w pełni kwalifikowanej nazwy. Elementy te można wywołać przy użyciu następującej składni: `Class["MemberName"](parameter)`.  
  
     W poniższym kodzie dwa interfejsy ma metody rysowania i dotyczą obu interfejsów implementuje klasy środowiska wykonawczego.  
  
    ```cpp#  
    namespace CollisionExample {  
        interface InterfaceA  
        {  
            HRESULT Draw([in] Int32 a);  
        }  
        interface InterfaceB  
        {  
            HRESULT Draw([in] HString a);  
        }  
        runtimeclass ExampleObject {  
          interface InterfaceA  
          interface InterfaceB  
        }  
    }  
    ```  
  
     Oto, jak można wywołać powyżej kodu w języku JavaScript.  
  
    ```JavaScript  
    var example = new ExampleObject();  
    example["CollisionExample.InterfaceA.draw"](12);  
    example["CollisionExample.InterfaceB.draw"]("hello");  
    ```  
  
-   `Out`Parametry: Jeśli metoda środowiska uruchomieniowego systemu Windows ma wiele `out` parametrów, w języku JavaScript metody ma obiekt JavaScript jako jego wartość zwrotna, a obiekt ma właściwości, które odpowiadają `out` parametru. Na przykład należy wziąć pod uwagę następujące podpisu środowiska wykonawczego systemu Windows w języku C++.  
  
    ```cpp#  
    void ExampleMethod(  
      [OutAttribute] char^ first,   
      [OutAttribute] char^ second  
    )  
    ```  
  
     Wersja języka JavaScript podpis jest:  
  
    ```JavaScript  
    var returnValue = exampleMethod();  
  
    ```  
  
     W tym przykładzie `returnValue` jest obiektem JavaScript, która ma dwa pola: `first` i `second`.  
  
-   Statyczne elementy członkowskie: definiuje środowiska wykonawczego systemu Windows zarówno statycznych elementów członkowskich i elementów członkowskich wystąpień. W języku JavaScript statyczne elementy członkowskie są dodawane do obiektu, który jest skojarzony z klasy środowiska wykonawczego systemu Windows lub interfejs.  
  
    ```JavaScript  
    // Static method.   
    var accel = Windows.Devices.Sensors.Accelerometer.getDefault();   
    // Instance method.   
    var reading = accel.getCurrentReading();            
    ```  
  
 Aby uzyskać więcej informacji na temat JavaScript reprezentację podstawowych typów środowiska wykonawczego systemu Windows, temacie [JavaScript reprezentacja środowiska wykonawczego systemu Windows typy](../jswinrt/javascript-representation-of-windows-runtime-types.md).