---
title: Refaktoryzacji kodu języka Python
description: Jak można łatwo zrefaktoryzuj kod języka Python w programie Visual Studio zmieniając identyfikatory wyodrębniania metody, importy Dodawanie i usuwanie nieużywanych importuje.
ms.date: 06/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: c756e92b6abc383cb4515a628fb81308e21a1f01
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37056543"
---
# <a name="refactoring-python-code"></a>Refaktoryzacji kodu języka Python

Program Visual Studio udostępnia kilka polecenia automatycznie Przekształcanie i czyszczenie kodu źródłowego języka Python:

- [Zmień nazwę](#rename) zmienia nazwę wybranej klasy, metody lub nazwę zmiennej
- [Wyodrębnij metodę](#extract-method) tworzy nową metodę z zaznaczonym kodzie
- [Dodaj importu](#add-import) zapewnia tagów inteligentnych można dodać brakujące importu
- [Usuń nieużywane importów](#remove-unused-imports) Usuwa nieużywane importów

<a name="rename-variable"</a>

## <a name="rename"></a>Zmień nazwę

1. Kliknij prawym przyciskiem myszy identyfikator chcesz zmienić nazwę i wybierz **zmienić**, lub ustaw karetkę identyfikator i wybierz **Edytuj > Refaktoryzuj > Zmień nazwę...**  polecenia menu (F2).
1. W **zmienić** okno dialogowe zostanie wyświetlone, wprowadź nową nazwę dla identyfikatora i wybierz **OK**:

  ![Zmień nazwę monit o podanie nowej nazwy identyfikatora](media/code-refactor-rename-1.png)

1. W następnym oknie dialogowym Wybierz pliki i wystąpień w kodzie, do której można zastosować zmianę nazwy; Wybierz poszczególne wystąpienie do podglądu określonych zmian:

  ![Zmień nazwę okna dialogowego, aby wybrać miejsce zastosować zmiany](media/code-refactor-rename-2.png)

1. Wybierz **Zastosuj** będzie wprowadzenie zmian do plików kodu źródłowego. (Ta akcja może być cofnięte).

## <a name="extract-method"></a>Wyodrębnianie metody

1. Wybierz wiersze, kodu lub wyrażenie, które ma wyodrębnić w oddzielnych metodach.
1. Wybierz **Edytuj > Refaktoryzuj > wyodrębniania metody...**  polecenia menu lub typ Ctrl-R, M.
1. W oknie dialogowym wprowadź nową nazwę metody, wskaż, gdzie go do wyodrębnienia, a następnie wybierz zmiennych zamknięcia. Zmienne, które nie zostały wybrane do zamknięcia są przekształcane w argumenty metody:

  ![Wyodrębnij okna dialogowego — metoda](media/code-refactor-extract-method-1.png)

1. Wybierz **OK** i kod został zmodyfikowany w związku z tym:

  ![Efekt wyodrębniania metody](media/code-refactor-extract-method-2.png)

## <a name="add-import"></a>Dodaj importu

Po umieszczeniu karetkę na identyfikator nie ma informacji o typie program Visual Studio udostępnia tagów inteligentnych (ikona żarówka na lewo od kodu) której polecenia Dodaj niezbędne `import` lub `from ... import` instrukcji:

![Dodawanie tagów inteligentnych importu](media/code-refactor-add-import-1.png)

Program Visual Studio oferuje `import` zakończeń pakietów najwyższego poziomu i modułów w bieżącym projekcie i bibliotekę standardową. Visual Studio oferuje również `from ... import` zakończeń dla modułów podrzędnych i podpakietów, jak również członkowie modułu. Zakończeń obejmują funkcje, klas lub wyeksportowane dane. Wybierając jedną z opcji dodaje instrukcji w górnej części pliku po innych importów lub do istniejącej `from ... import` instrukcję, jeśli w tym samym module jest już zaimportowana.

![Wynikiem dodania do importu](media/code-refactor-add-import-2.png)

Visual Studio próbuje odfiltrować elementy członkowskie, które faktycznie nie są zdefiniowane w module, takie jak moduły, które zostały zaimportowane do innego, ale nie są elementami podrzędnymi podczas importowania modułu. Na przykład użyć wielu modułów `import sys` zamiast `from xyz import sys`, więc nie widzisz zakończenia importowania `sys` z innymi modułami, nawet jeśli brakuje modułów `__all__` elementu członkowskiego, który wyklucza `sys`.

Podobnie Visual Studio filtruje funkcje, które są importowane z innymi modułami lub wbudowanych przestrzeni nazw. Na przykład jeśli importuje moduł `settrace` funkcji z `sys` moduł, a następnie teoretycznie można importować go z tego modułu. Ale najlepiej użyć `import settrace from sys` bezpośrednio, co program Visual Studio oferuje specjalnie tej instrukcji.

Ponadto jeśli coś zwykle można wykluczyć, ale ma inne wartości, które będą uwzględnione (ponieważ jest to nazwa została przypisana wartość w module, na przykład), programu Visual Studio nadal wyklucza importu. To zachowanie przyjęto założenie, że wartość nie należy można wyeksportować, ponieważ jest on zdefiniowany w innym module, i w związku z tym dodatkowe przypisania mogą być również wyeksportowany nie fikcyjnej wartości.

<a name="remove-imports"</a>

## <a name="remove-unused-imports"></a>Usuń nieużywane importów

Podczas pisania kodu, jest łatwo tworzyć `import` instrukcje dla modułów, które nie są używane w ogóle. Ponieważ program Visual Studio analizuje kodu, automatycznie można określić czy `import` instrukcji jest potrzebna, analizując czy importowany nazwa jest używana w zakresie, poniżej której występuje instrukcja.

Kliknij prawym przyciskiem myszy w edytorze i wybierz **Usuń importów**, które zapewnia opcje, aby usunąć z **wszystkie zakresy** lub po prostu **bieżącego zakresu**:

![Usuń importuje menu](media/code-refactor-remove-imports-1.png)

Visual Studio podejmuje odpowiednie zmiany w kodzie:

![Wpływ usunięcia importów](media/code-refactor-remove-imports-2.png)

Należy pamiętać, że program Visual Studio bez uwzględnienia przepływu sterowania; przy użyciu nazwy przed `import` instrukcji jest traktowany jak nazwa w rzeczywistości była używana. Visual Studio również ignoruje wszystkie `from __future__` Importy, Importy, które są wykonywane wewnątrz definicji klasy, jak również z `from ... import *` instrukcje.