---
title: Wstawki kodu programu Visual C++ kod
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CPP
ms.workload:
- cplusplus
ms.openlocfilehash: bb091701384d36ca5aa8154701d94cda5fb34a5b
ms.sourcegitcommit: a8e01952be5a539104e2c599e9b8945322118055
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="visual-c-code-snippets"></a>Wstawki kodu programu Visual C++ kod

W programie Visual Studio można wstawki kodu Dodaj kod najczęściej używanych do plików kodu C++. Ogólnie rzecz biorąc można użyć wstawki kodu w podobny sposób jak w języku C#, ale różni się zbiór domyślne wstawki kodu.

Możesz dodać fragment kodu w określonej lokalizacji w kodzie (wstawiania) lub przestrzenny niektórych zaznaczony kod z fragment kodu.

## <a name="insert-a-code-snippet"></a>Wstawianie wstawek kodu

Aby wstawić fragment kodu, otwórz plik kodu C++ (*.cpp* lub *.h*), kliknij dowolne miejsce w pliku, i wykonaj jedną z następujących czynności:

- Kliknij prawym przyciskiem myszy, aby uzyskać menu kontekstowe i wybierz **wstawić fragment kodu**

- W **edycji / IntelliSense** menu, wybierz opcję **wstawić fragment kodu**

- Użyj klawiszy dostępu: **Ctrl**+**K**+**X**

Powinna wyświetlić się lista dostępnych opcji, począwszy od **#if**. Po wybraniu **#if**, powinien zostać wyświetlony następujący kod dodane do pliku:

```cpp
#if 0

#endif // 0
```

Następnie można zastąpić **0** z warunkiem poprawne.

## <a name="use-a-code-snippet-to-surround-selected-code"></a>Otaczające zaznaczony kod za pomocą wstawek kodu

Aby użyć fragment kodu otaczającego zaznaczony kod, wybierz wiersz (lub wiele wierszy) i wykonaj jedną z następujących czynności:

- Kliknij prawym przyciskiem myszy, aby uzyskać menu kontekstowego, a następnie wybierz **z funkcji Otocz przez**

- Z **Edytuj** > **IntelliSense** menu, wybierz opcję **z funkcji Otocz przez**

- Przy użyciu klawiatury, naciśnij klawisz: **Ctrl**+**K**+**S**

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

**Klasy** fragment kodu zawiera definicję klasy o nazwie `MyClass`, z odpowiednich domyślny konstruktor i destruktor, gdy definicje Konstruktor i destruktor znajdują się poza klasy:

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

**Classi** fragment kodu udostępnia również definicję klasy o nazwie `MyClass`, ale domyślny konstruktor i destruktor są zdefiniowane w definicji klasy:

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

Po wstawieniu fragmentu destruktora zapewnia destruktor dla elementu `SomeClass`:

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

- [Fragmenty kodu](../ide/code-snippets.md)