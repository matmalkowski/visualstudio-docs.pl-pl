---
title: "Tworzenie testu jednostkowego klas zastępczych metody przy użyciu polecenia Utwórz testy jednostkowe | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: unit testing, create unit tests
ms.assetid: 5D625021-BA96-48A5-9453-3EF6F0943466
caps.latest.revision: "56"
ms.author: douge
manager: douge
ms.openlocfilehash: 7e69218700314224f67094486cfd381ac1460995
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="create-unit-test-method-stubs-with-the-create-unit-tests-command"></a>Utwórz jednostki klas zastępczych metody testu za pomocą polecenia Utwórz testy jednostkowe

Visual Studio **tworzenia testów jednostkowych** polecenie umożliwia tworzenie jednostki klas zastępczych metody testu. Ta funkcja umożliwia łatwe konfigurację projektu testowego, klasy testowej i szkieletu metody testu w niej. 

## <a name="availability-and-extensions"></a>Dostępność i rozszerzenia

**Tworzenia testów jednostkowych** polecenie:

* Jest dostępny w Community, Professional i Enterprise wersje programu Visual Studio 2015 i nowszych.

* Obsługuje tylko kodu C# przeznaczonego dla programu .NET Framework.

* Jest [extensible](#extend-framework)i obsługuje emitowanie testów w MSTest, MSTest V2, NUnit, xUnit format.

## <a name="get-started"></a>Wprowadzenie

Aby rozpocząć, wybierz metodę, typu lub przestrzeni nazw w edytorze kodu w projekcie, aby przetestować, otwórz menu skrótów i wybierz polecenie **tworzenia testów jednostkowych**. Spowoduje to otwarcie **tworzenia testów jednostkowych** okna dialogowego, w którym można wybrać opcje tworzenia nowych testów jednostkowych.

![Za pomocą polecenia Create testy jednostkowe](media/createunittestcommand.png)

## <a name="setting-unit-test-traits"></a>Ustawienie cech testów jednostkowych

Jeśli planujesz uruchamianie tych testów wchodzi w skład procesu automatyzacji testów, warto rozważyć o teście utworzony w innym projekcie testowym (druga opcja w oknie dialogowym powyżej) i testów jednostkowych ustawienie cech dla testu jednostkowego. Umożliwi to łatwiej dołączania lub wykluczania tych określonych testów w ramach ciągłej integracji lub potoku ciągłego wdrażania. Cechy są ustawiane przez dodanie metadanych do testu jednostkowego bezpośrednio, jak pokazano poniżej. 

![Ustawienie cech testów jednostkowych](media/createunittest.png)

<a name="extend-framework"></a>
## <a name="using-third-party-unit-test-frameworks"></a>Przy użyciu platform testów jednostkowych innych firm

Program Visual Studio mogą być utworzone przy użyciu dowolnej struktury testowej testów jednostkowych. Aby zainstalować Dodaj inne struktury testu, wybierz **narzędzia | Rozszerzenia i aktualizacje**.
Rozwiń węzeł **Online**, **galerii programu Visual Studio**, **narzędzia**i wybierz polecenie **testowanie**. 

![Przy użyciu innej platform testów](media/createunittestfx.png)

Test framework rozszerzenia są dostępne w programie Visual Studio Marketplace:

* [Rozszerzenie NUnit generatory testu](https://marketplace.visualstudio.com/items?itemName=NUnitDevelopers.TestGeneratorNUnitextension)
* [Rozszerzenie xUnit.net generatory testu](https://marketplace.visualstudio.com/items?itemName=BradWilson.xUnitnetTestExtensions)

## <a name="when-should-i-use-this-feature"></a>Kiedy należy używać tej funkcji?

Ta funkcja zawsze, gdy trzeba utworzyć testy jednostek, ale w szczególności, podczas testowania istniejącego kodu nie ma bardzo mało lub nie pokrycie testu, a nie dokumentacji. Innymi słowy przypadku Specyfikacja kodu ograniczony lub nie istnieje. Efektywne implementuje podejście podobne do [inteligentnych testów jednostkowych](http://blogs.msdn.com/b/visualstudioalm/archive/2014/11/19/introducing-smart-unit-tests.aspx) charakteryzuje się obserwowanych zachowania kodu.

Jednak ta funkcja jest równie mające zastosowanie do sytuacji, w którym rozpoczyna się przez napisanie kodu dewelopera, a użyty do ładowania początkowego testowania dyscypliny jednostek. W ramach przepływu kodowania deweloper może być szybko utworzyć jednostki testu szkieletu metody (z klasy odpowiedniego testu, a Projekt testowy odpowiedniego) dla określonej części kodu. 

## <a name="more-information"></a>Więcej informacji

Zobacz wpis w blogu [tworzenie testu jednostkowego klas zastępczych metody przy użyciu "Tworzenia testów jednostkowych"](https://blogs.msdn.microsoft.com/visualstudioalm/2015/03/06/creating-unit-test-method-stubs-with-create-unit-tests/).

Można znaleźć więcej testowania blogach jednostek [tutaj](https://blogs.msdn.microsoft.com/visualstudioalm/tag/unit-testing/).
