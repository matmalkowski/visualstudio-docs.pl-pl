---
title: Tworzenie projektu testu jednostkowego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a608bfba-1a43-4a60-b73a-1fe53ef58098
caps.latest.revision: 10
ms.author: gewarren
manager: douge
ms.openlocfilehash: eb9c64fca2bcd4086073fc349d2c81fa2a62be31
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42681904"
---
# <a name="create-a-unit-test-project"></a>Tworzenie projektu testu jednostkowego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [Tworzenie projektu testu jednostkowego](https://docs.microsoft.com/visualstudio/test/create-a-unit-test-project).  
  
Testy jednostkowe dublowanie często struktury kodu w ramach testu. Na przykład projekt testu jednostkowego zostałyby utworzone dla każdego projektu kodu, w ramach produktu. Projekt testowy może znajdować się w tym samym rozwiązaniu, jak kod w środowisku produkcyjnym lub może być w oddzielnym rozwiązaniu. Może mieć wiele jednostek projekty testowe w rozwiązaniu.  
  
> [!NOTE]
>  Lokalizacja jednostek testów dla kodu natywnego i struktura projektu testowego może być inna niż strukturę, która jest opisane w tym temacie. Aby uzyskać więcej informacji, zobacz [Dodawanie testów jednostkowych do istniejących aplikacji C++](../test/unit-testing-existing-cpp-applications-with-test-explorer.md).  
  
## <a name="to-create-a-unit-test-project"></a>Aby utworzyć projekt testów jednostkowych:  
  
1.  Na **pliku** menu, wybierz **New** , a następnie wybierz **projektu** (klawiatura: Ctrl + Shift + N).  
  
2.  W oknie dialogowym Nowy projekt rozwiń **zainstalowane** węzła, wybierz język, którego chcesz użyć dla projektu testowego, a następnie wybierz **testu**.  
  
3.  Aby użyć jednego z platform testów jednostkowych firmy Microsoft, wybierz opcję **projektu testu jednostkowego** z listy szablonów projektu. W przeciwnym razie wybierz szablon projektu jednostki środowiskiem testowym, którego chcesz użyć. Aby przetestować projekt kont w naszym przykładzie, czy nazwa projektu AccountsTests.  
  
4.  W projekcie testu jednostki Dodaj odwołanie do testowanego kodu.  Oto jak utworzyć odwołanie do projektu kodu w tym samym rozwiązaniu:  
  
    1.  Wybierz projekt w Eksploratorze rozwiązań.  
  
    2.  Na **projektu** menu, wybierz **Dodaj odwołanie...** .  
  
    3.  W oknie dialogowym Reference Manager Otwórz **rozwiązania** węzeł i wybierz polecenie **projektów**. Sprawdź nazwę projektu kodu, a następnie zamknij okno dialogowe.  
  
5.  Jeśli kod, który ma zostać przetestowana, jest w innej lokalizacji, zobacz [Zarządzanie odwołaniami w projekcie](../ide/managing-references-in-a-project.md) informacje dotyczące dodawania odwołania.  
  
## <a name="next-steps"></a>Następne kroki  
 **Pisanie testów jednostkowych**  
  
 Zobacz jeden z następujących sekcji:  
  
-   [Pisanie testów jednostkowych dla .NET Framework za pomocą struktury testów jednostkowych Microsoft dla kodu zarządzanego](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)  
  
-   [Pisanie testów jednostkowych dla języka C/C++ za pomocą Frameworka testów jednostkowych firmy Microsoft dla języka C++](../test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp.md)  
  
 **Uruchamianie testów jednostkowych**  
  
 [Przeprowadzanie testów jednostkowych za pomocą narzędzia Eksplorator testów](../test/run-unit-tests-with-test-explorer.md)



