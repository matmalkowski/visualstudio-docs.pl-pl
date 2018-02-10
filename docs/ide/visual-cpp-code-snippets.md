---
title: Wstawki kodu Visual C++ | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs:
- CPP
ms.workload:
- cplusplus
ms.openlocfilehash: b2a8b1c99d1b084a6f8d3c050302e16ea40d64ac
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="visual-c-code-snippets"></a>Wstawki kodu programu Visual C++ kod

W programie Visual Studio można wstawki kodu Dodaj kod najczęściej używanych do plików kodu C++. Ogólnie rzecz biorąc można użyć wstawki kodu w podobny sposób jak w języku C#, ale różni się zbiór domyślne wstawki kodu.

Możesz dodać fragment kodu w określonej lokalizacji w kodzie (wstawiania) lub przestrzenny niektórych zaznaczony kod z fragment kodu.

## <a name="inserting-a-code-snippet"></a>Wstawianie wstawek kodu

Aby wstawić fragment kodu, otwórz plik kodu C++ (.cpp lub .h), kliknij dowolne miejsce w pliku i wykonaj jedną z następujących czynności:

- Kliknij prawym przyciskiem myszy, aby uzyskać menu kontekstowe i wybierz **wstawić fragment kodu**

- W **edycji / IntelliSense** menu, wybierz opcję **wstawić fragment kodu**

- Użyj klawiszy dostępu: **Ctrl**+**K**+**X**

Powinna wyświetlić się lista dostępnych opcji, począwszy od **#if**. Po wybraniu **#if**, powinien zostać wyświetlony następujący kod dodane do pliku:

```cpp
#if 0

#endif // 0
```

Następnie można zastąpić 0 z warunkiem poprawne.

## <a name="using-a-code-snippet-to-surround-selected-code"></a>Otaczające zaznaczony kod za pomocą wstawek kodu

Aby użyć fragment kodu otaczającego zaznaczony kod, wybierz wiersz (lub wiele wierszy) i wykonaj jedną z następujących czynności:

- Kliknij prawym przyciskiem myszy, aby uzyskać menu kontekstowego, a następnie wybierz **z funkcji Otocz przez**

- Z **Edytuj** > **IntelliSense** menu, wybierz opcję **z funkcji Otocz przez**

- Przy użyciu klawiatury, naciśnij klawisz: **CTRL**+**K**+**S**

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

**Classi** fragment kodu udostępnia również definicję klasy o nazwie MyClass, ale domyślny konstruktor i destruktor są zdefiniowane w definicji klasy:

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

## <a name="for-vs-forr-vs-rfor"></a>Aby uzyskać porównanie forr vs rfor

Istnieją trzy różne **dla** fragmentów zawierających różne rodzaje z `for` pętli.

**Rfor** fragment kodu udostępnia [opartej na zakresie](/cpp/cpp/range-based-for-statement-cpp) dla pętli (łącze). Ta konstrukcja jest preferowane opartego na indeksie `for` pętli.

```cpp
for (auto& i : v)
{

}
```

**Dla** fragment kodu udostępnia `for` pętli, w którego warunku jest oparty na długość (w `size_t`) obiektu.

```cpp
for (size_t i = 0; i < length; i++)
{

}
```

**Forr** fragment kodu udostępnia reverse `for` pętli, w którego warunku jest oparty na długość (w postaci liczb całkowitych) obiektu.

```cpp
for (int i = length - 1; i >= 0; i--)
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

## <a name="see-also"></a>Zobacz także

[Fragmenty kodu](../ide/code-snippets.md)
