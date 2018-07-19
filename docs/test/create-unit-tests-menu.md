---
title: Tworzenie wycinków kodu metoda testu jednostki w programie Visual Studio
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- unit testing, create unit tests
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 652a9595601c614d18daf175a72404f9570d4162
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/17/2018
ms.locfileid: "39078332"
---
# <a name="create-unit-test-method-stubs-with-the-create-unit-tests-command"></a>Tworzenie jednostki wycinki kodu metoda testu za pomocą polecenia Utwórz testy jednostkowe

Visual Studio **Utwórz testy jednostkowe** polecenie zapewnia możliwość tworzenia wycinków kodu metoda testu jednostki. Ta funkcja umożliwia Łatwa konfiguracja projektu testowego, klasy testowej i testu zastępczego metoda znajdujący się w nim.

## <a name="availability-and-extensions"></a>Dostępność i rozszerzenia

**Utwórz testy jednostkowe** polecenia menu:

* Jest dostępne w Community, Professional i Enterprise wersje programu Visual Studio 2015 i nowszych wersjach.

* Obsługuje tylko C# kod, który jest przeznaczony dla .NET Framework.

* Jest wszechstronne i obsługuje emitowanie testów MSTest, MSTest w wersji 2, NUnit, xUnit format.

* Nie jest jeszcze dostępna w projektach .NET Core.

## <a name="get-started"></a>Wprowadzenie

Aby rozpocząć, wybierz metodę, typu lub przestrzeni nazw w edytorze kodu w projekcie, aby test, otwórz menu skrótów i wybierz **Utwórz testy jednostkowe**. **Utwórz testy jednostkowe** zostanie otwarte okno dialogowe, gdy można wybrać opcję Utwórz nowe testy jednostkowe.

![Za pomocą polecenia Utwórz testy jednostki](media/createunittestcommand.png)

## <a name="setting-unit-test-traits"></a>Ustawienie cech testu jednostki

Jeśli planujesz uruchomić te testy jako część procesu automatyzacji testów, należy rozważyć, posiadające testu, utworzone w innym projekcie testowym (druga opcja w oknie dialogowym powyżej) i testów jednostkowych ustawienie cech dla testu jednostkowego. Dzięki temu można łatwiej lub wykluczane z tych określonych testów w ramach ciągłej integracji i ciągłego wdrażania potoku. Cechy są ustawiane przez dodanie metadanych do testu jednostkowego bezpośrednio, jak pokazano poniżej.

![Ustawienie cech testu jednostki](media/createunittest.png)

## <a name="using-third-party-unit-test-frameworks"></a>Za pomocą platform testów jednostkowych innych firm

Za pomocą programu Visual Studio mogą być testy jednostkowe, utworzony za pomocą dowolnej platformy testów. Aby zainstalować inne struktury testów:

1. Wybierz **narzędzia** > **rozszerzenia i aktualizacje**.
2. Rozwiń **Online** > **Visual Studio Marketplace** > **narzędzia**, a następnie wybierz **testowania**.

![Za pomocą platform testowych innych firm](media/createunittestfx.png)

Rozszerzenia ramy testów są dostępne w Visual Studio Marketplace:

* [Rozszerzenie NUnit dla generatorów testu](https://marketplace.visualstudio.com/items?itemName=NUnitDevelopers.TestGeneratorNUnitextension)
* [rozszerzenie xUnit.net dla generatorów testu](https://marketplace.visualstudio.com/items?itemName=BradWilson.xUnitnetTestExtensions)

## <a name="when-should-i-use-this-feature"></a>Kiedy należy używać tej funkcji?

Ta funkcja zawsze, gdy trzeba utworzyć testy jednostkowe, ale szczególnie w przypadku, gdy testujesz istniejący kod, który ma niewielkiego lub żadnego pokrycie testu i nie dokumentacji. Innymi słowy gdy specyfikacja ograniczony lub nieistniejącego kodu. Skutecznie implementuje podejście podobne do [inteligentne testy jednostkowe](http://blogs.msdn.com/b/visualstudioalm/archive/2014/11/19/introducing-smart-unit-tests.aspx) charakteryzuje się obserwacji zachowania kodu.

Jednak ta funkcja jest równie dotyczy sytuacji, gdzie rozpoczyna się przez pisanie kodu dla deweloperów, a użyty do uruchamiania testów dyscypliny jednostkowych. W ramach przepływu kodowania deweloper może być szybko tworzyć jednostki metoda zastępcza klasa testowa (z klasą testową odpowiednie, a Projekt testowy odpowiednie) dla określonego fragmentu kodu.

## <a name="see-also"></a>Zobacz także

- [Tworzenie wycinków metody testów jednostkowych za pomocą "Utwórz testy jednostkowe"](https://blogs.msdn.microsoft.com/visualstudioalm/2015/03/06/creating-unit-test-method-stubs-with-create-unit-tests/)
- [Wpisy w blogu testy jednostkowe](https://blogs.msdn.microsoft.com/devops/?s=unit+testing)
