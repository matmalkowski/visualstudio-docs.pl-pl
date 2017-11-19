---
title: Wstawki kodu Visual C++ | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 74e26fd4-e5ca-4611-a816-0a521b4947a0
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0d9a34e371797317d3163f8288474e7a902b4f82
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="visual-c-code-snippets"></a>Wstawki kodu języka Visual C++
W programie Visual Studio można wstawki kodu Dodaj kod najczęściej używanych do plików kodu C++. Ogólnie rzecz biorąc można użyć wstawki kodu w podobny sposób jak w języku C#, ale różni się zbiór domyślne wstawki kodu.  
  
 Możesz dodać fragment kodu w określonej lokalizacji w kodzie (wstawiania) lub przestrzenny niektórych zaznaczony kod z fragment kodu.  
  
## <a name="inserting-a-code-snippet"></a>Wstawianie wstawek kodu  
 Aby wstawić fragment kodu, otwórz plik kodu C++ (.cpp lub .h), kliknij dowolne miejsce w pliku i wykonaj jedną z następujących czynności:  
  
-   Kliknij prawym przyciskiem myszy, aby uzyskać menu kontekstowe i wybierz **wstawić fragment kodu**  
  
-   W **edycji / IntelliSense** menu, wybierz opcję **wstawić fragment kodu**  
  
-   Użyj klawiszy dostępu: **CTRL + K + X**  
  
 Powinna wyświetlić się lista dostępnych opcji, począwszy od **#if**. Po wybraniu **#if**, powinien zostać wyświetlony następujący kod dodane do pliku:  
  
```cpp  
#if 0  
  
#endif // 0  
```  
  
 Następnie można zastąpić 0 z warunkiem poprawne.  
  
## <a name="using-a-code-snippet-to-surround-selected-code"></a>Przy użyciu fragment kodu otaczającego zaznaczony kod  
 Aby użyć fragment kodu otaczającego zaznaczony kod, wybierz wiersz (lub wiele wierszy) i wykonaj jedną z następujących czynności:  
  
1.  Kliknij prawym przyciskiem myszy, aby uzyskać menu kontekstowe i wybierz **z funkcji Otocz przez**  
  
2.  W **edycji / IntelliSense** menu, wybierz opcję **z funkcji Otocz przez**  
  
3.  Użyj klawiszy dostępu: **CTRL + K + S**  
  
 Wybierz **#if**. Powinny pojawić się dane podobne do poniższych:  
  
```cpp  
#if 0  
#include "pch.h"  // or whatever line you had selected  
#endif // 0  
```  
  
 Następnie można zastąpić 0 z warunkiem poprawne.  
  
## <a name="where-can-i-find-a-complete-list-of-the-c-code-snippets"></a>Gdzie można znaleźć pełną listę fragmentów kodu C++  
 Pełną listę fragmentów kodu C++ można znaleźć, przechodząc do **Menedżerze fragmentów kodu** (na **narzędzia** menu), a ustawienie **języka** do **Visual C++** . W polu poniżej, rozwiń węzeł **Visual C++**. Powinny pojawić się nazwy wszystkich fragmentów kodu C++ w kolejności alfabetycznej.  
  
 Nazwy większości fragmentów kodu nie wymaga wyjaśnień, ale niektóre nazwy mogą być mylące.  
  
## <a name="class-vs-classi"></a>Klasa a classi  
 **Klasy** fragment kodu zawiera definicję klasy o nazwie MyClass, destruktor, gdy definicje Konstruktor i destruktor znajdują się poza klasą i odpowiedni konstruktor domyślny:  
  
```cpp  
class MyClass  
{  
public:  
MyClass();  
~MyClass();  
  
private:  
  
};  
  
MyClass::MyClass()  
{  
}  
  
MyClass::~MyClass()  
{  
}  
```  
  
 Fragment kodu classi udostępnia również definicję klasy o nazwie MyClass, ale domyślny konstruktor i destruktor są zdefiniowane w definicji klasy:  
  
```cpp  
class MyClass  
{  
public:  
MyClass()  
{  
}  
  
~MyClass()  
{  
}  
  
private:  
  
};  
```  
  
## <a name="for-vs-foreach-vs-forr-vs-rfor"></a>Aby uzyskać porównanie foreach a forr vs rfor  
 Istnieją cztery różne dla fragmentów zawierających różne rodzaje z dla pętli.  
  
 **Dla** fragment kodu udostępnia `for` pętli, w którego warunku jest oparty na długość (w `size_t`) obiektu:  
  
```cpp  
for (size_t i = 0; i < length; i++)  
{  
  
}  
```  
  
 **Foreach** fragment kodu udostępnia `for each` pętlę iterującą przez członków kolekcji:  
  
```cpp  
for each (object var in collection_to_loop)  
{  
  
}  
```  
  
 **Forr** fragment kodu udostępnia reverse `for` pętli, w którego warunku jest oparty na długość (w postaci liczb całkowitych) obiektu:  
  
```cpp  
for (int i = length - 1; i >= 0; i--)  
{  
  
}  
```  
  
 **Rfor** fragment kodu udostępnia [opartej na zakresie](/cpp/cpp/range-based-for-statement-cpp) dla pętli (łącze):  
  
```cpp  
for (auto& i : v)  
{  
  
}  
```  
  
## <a name="the-destructor-snippet-"></a>Fragment — destruktor (~)  
 Fragment kodu — destruktor (**~**) zawiera inaczej w różnych kontekstach. Po wstawieniu ta Wstawka kodu wewnątrz klasy zawiera destruktora dla tej klasy. Przykładowo podana następujący kod:  
  
```cpp  
class SomeClass {  
  
};  
```  
  
 Po wstawieniu fragmentu destruktora zapewnia destruktora SomeClass:  
  
```cpp  
class SomeClass {  
    ~SomeClass()  
    {  
  
    }  
};  
```  
  
 Jeśli podczas próby wstawienia fragment destruktora poza klasą, zapewnia destruktora o nazwie symbolu zastępczego:  
  
```cpp  
~TypeNamePlaceholder()  
{  
  
```