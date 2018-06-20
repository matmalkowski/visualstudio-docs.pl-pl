---
title: Tworzenie projektu testu jednostki w programie Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 3dc86281542dbedd429fae5f9976219bfa623878
ms.sourcegitcommit: f685fa5e2df9dc307bf1230dd9dc3288aaa408b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2018
ms.locfileid: "36235053"
---
# <a name="create-a-unit-test-project"></a>Tworzenie projektu testu jednostkowego

Testy jednostkowe często duplikatów struktury kodu w ramach testu. Na przykład jednostkowy projekt testowy zostałyby utworzone dla każdego projektu kodu, w ramach produktu. Projekt testowy może znajdować się w tym samym rozwiązaniu jako kodzie produkcyjnym lub może być w oddzielnym rozwiązaniu. Może mieć wiele jednostek testowanie projektów w rozwiązaniu.

> [!NOTE]
> Lokalizacja jednostki testów dla kodu natywnego i struktury projektu testowego może być inna niż struktury, które jest opisane w tym temacie. Aby uzyskać więcej informacji, zobacz [dla C/C++ pozwala pisać testy jednostkowe](writing-unit-tests-for-c-cpp.md).

## <a name="to-create-a-unit-test-project"></a>Aby utworzyć jednostkowy projekt testowy:

1.  Na **pliku** menu, wybierz **nowy** , a następnie wybierz **projektu** (klawiatury **Ctrl**+**Shift** + **N**).

2.  W **nowy projekt** okna dialogowego rozwiń **zainstalowana** węzła, wybierz język, którego chcesz użyć dla projektu testowego, a następnie wybierz **testu**.

3.  Aby użyć jednego z platform testów jednostkowych firmy Microsoft, wybierz **projektu testu jednostki** z listy szablonów projektu. W przeciwnym razie wybierz szablon projektu jednostki struktury testowej, która ma być używany. Aby przetestować projekt kont w naszym przykładzie, czy nazwa projektu **AccountsTests**.

4.  W jednostkowy projekt testowy Dodaj odwołanie do kodu w ramach testu.  Poniżej przedstawiono sposób utworzyć odwołanie do projektu kodu, w tym samym rozwiązaniu:

    1.  Wybierz projekt **Eksploratora rozwiązań**.

    2.  Na **projektu** menu, wybierz **Dodaj odwołanie**.

    3.  W **Menedżera odwołań** po otwarciu okna dialogowego **rozwiązania** węzeł i wybierz polecenie **projekty**. Sprawdź nazwę projektu kodu i zamknąć okno dialogowe.

5.  Jeśli kod, który ma zostać przetestowana, jest w innej lokalizacji, zobacz [Zarządzanie odwołaniami w projekcie](../ide/managing-references-in-a-project.md) informacje na temat dodawania odwołania.

## <a name="next-steps"></a>Następne kroki
 **Pisanie testów jednostkowych**

 Zobacz jedną z następujących sekcji:

-   [Kod testu jednostkowego](../test/unit-test-your-code.md)

-   [Pisanie testów jednostkowych dla C/C++](writing-unit-tests-for-c-cpp.md)

-   [Za pomocą architektury MSTest w testy jednostkowe](using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md)

 **Uruchamianie testów jednostkowych**

- [Przeprowadzanie testów jednostkowych za pomocą narzędzia Eksplorator testów](../test/run-unit-tests-with-test-explorer.md)