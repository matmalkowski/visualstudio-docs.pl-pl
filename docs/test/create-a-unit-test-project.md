---
title: Tworzenie projektu testu jednostki w programie Visual Studio | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 998b936f33047d6132889a949a6ecd56f5a40911
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="create-a-unit-test-project"></a>Tworzenie projektu testu jednostkowego

Testy jednostkowe często duplikatów struktury kodu w ramach testu. Na przykład jednostkowy projekt testowy zostałyby utworzone dla każdego projektu kodu, w ramach produktu. Projekt testowy może znajdować się w tym samym rozwiązaniu jako kodzie produkcyjnym lub może być w oddzielnym rozwiązaniu. Może mieć wiele jednostek testowanie projektów w rozwiązaniu.

> [!NOTE]
>  Lokalizacja jednostki testów dla kodu natywnego i struktury projektu testowego może być inna niż struktury, które jest opisane w tym temacie. Aby uzyskać więcej informacji, zobacz [pisania testów jednostkowych dla C/C++](writing-unit-tests-for-c-cpp.md).

## <a name="to-create-a-unit-test-project"></a>Aby utworzyć jednostkowy projekt testowy:

1.  Na **pliku** menu, wybierz **nowy** , a następnie wybierz **projektu** (klawiatury Ctrl + Shift + N).

2.  W oknie dialogowym Nowy projekt, rozwiń węzeł **zainstalowana** węzła, wybierz język, którego chcesz użyć dla projektu testowego, a następnie wybierz **testu**.

3.  Aby użyć jednego z platform testów jednostkowych firmy Microsoft, wybierz **projektu testu jednostki** z listy szablonów projektu. W przeciwnym razie wybierz szablon projektu jednostki struktury testowej, która ma być używany. Aby przetestować projekt kont w naszym przykładzie, czy nazwa projektu AccountsTests.

4.  W jednostkowy projekt testowy Dodaj odwołanie do kodu w ramach testu.  Poniżej przedstawiono sposób utworzyć odwołanie do projektu kodu, w tym samym rozwiązaniu:

    1.  Wybierz projekt w Eksploratorze rozwiązań.

    2.  Na **projektu** menu, wybierz **Dodawanie odwołania...** .

    3.  W oknie dialogowym Menedżera odwołań, otwórz **rozwiązania** węzeł i wybierz polecenie **projekty**. Sprawdź nazwę projektu kodu i zamknąć okno dialogowe.

5.  Jeśli kod, który ma zostać przetestowana, jest w innej lokalizacji, zobacz [Zarządzanie odwołaniami w projekcie](../ide/managing-references-in-a-project.md) informacje na temat dodawania odwołania.

## <a name="next-steps"></a>Następne kroki
 **Pisanie testów jednostkowych**

 Zobacz jedną z następujących sekcji:

-   [Pisanie testów jednostkowych dla .NET Framework za pomocą struktury testów jednostkowych Microsoft dla kodu zarządzanego](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)

-   [Pisanie testów jednostkowych dla C/C++](writing-unit-tests-for-c-cpp.md)

 **Uruchamianie testów jednostkowych**

- [Przeprowadzanie testów jednostkowych za pomocą narzędzia Eksplorator testów](../test/run-unit-tests-with-test-explorer.md)