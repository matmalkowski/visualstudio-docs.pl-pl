---
title: Edytowanie testów obciążenia w programie Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Load Test Editor
- load tests, Load Test Editor
ms.assetid: ba16ed02-137e-40bf-a4cb-45d87d922d37
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 0841faf5e63b6c4108b9f65777416ded63227bb9
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/19/2018
ms.locfileid: "39152438"
---
# <a name="edit-load-tests"></a>Edytowanie testów obciążenia

Testy obciążenia są uruchamiane testy wydajności sieci Web lub testów jednostkowych, aby zasymulować wielu użytkownikom dostęp do serwera, w tym samym czasie. Test obciążeniowy umożliwia dostęp do danych obciążeniowych i wydajnościowych aplikacji. Test obciążeniowy można skonfigurować tak, aby emulował różne warunki obciążenia, np. obciążenie przez użytkowników i typy sieci.

> [!NOTE]
> Testowanie obciążenia jest dostępna tylko w wersji Enterprise programu Visual Studio 2017.

Test obciążenia jest definiowany przez *scenariuszy*, *zbiory liczników*, i *parametrów uruchomieniowych*. Na poniższej ilustracji wyjaśnia różnice między [scenariuszy](../test/edit-load-test-scenarios.md), [zbiory liczników](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md), i [parametrów uruchomieniowych](../test/load-test-run-settings-properties.md):

![Architektura testu obciążenia](../test/media/load_test_editor.png)

## <a name="edit-load-test-scenario-settings"></a>Edytowanie ustawień scenariusza testu obciążeniowego

Scenariusz służy do modelowania współdziałania grupy użytkowników z aplikacji serwera. Scenariusz składa się z wzorca obciążenia, modelu testu mieszanego, testu mieszanego, mieszanej przeglądarki i mieszanego profilu sieciowego. Test obciążeniowy może mieć więcej niż jeden scenariusz, a jeden scenariusz może zawierać testy wydajności sieci Web oraz testy jednostkowe. Grupując podobne ustawienia, scenariusz umożliwia łączenie i wspólne wykonywanie testów o podobnym charakterze.

Aby uzyskać więcej informacji, zobacz [scenariusze testów obciążenia edycji](../test/edit-load-test-scenarios.md) i [właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md).

## <a name="configure-and-manage-performance-counter-sets"></a>Konfigurowanie i zarządzanie zbiorami liczników wydajności

Testy obciążenia dostarczają nazwanych zestawów licznika, uporządkowanych według technologii, które są przydatne podczas analizowania danych licznika wydajności. Zestawy liczników obejmują Test obciążenia, IIS, ASP.NET i SQL. Po utworzeniu testu obciążenia za pomocą **Kreatora nowego testu obciążeniowego**, początkowy zestaw wstępnie zdefiniowanych i ważnych liczników jest skonfigurowany dla komputerów, które określono jako uwzględniane w teście obciążeniowym. Zarządzasz licznikami w **edytora testu obciążenia**.

Aby uzyskać więcej informacji, zobacz [Określanie zbiorów liczników oraz zasad progu dla komputerów w teście obciążeniowym](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

## <a name="configure-and-manage-load-test-run-settings"></a>Konfigurowanie i zarządzanie nimi uruchomieniowych testu obciążeniowego

Ustawienia uruchamiania są właściwości, które mają wpływ na sposób, w jaki przebieg testu obciążeniowego. Ustawienia uruchamiania są zorganizowane według kategorii w **właściwości** okna.

Aby uzyskać więcej informacji, zobacz [parametrów uruchomieniowych testu obciążeniowego Konfiguruj](../test/configure-load-test-run-settings.md) i [właściwości ustawień przebiegu testu obciążenia](../test/load-test-run-settings-properties.md).

## <a name="see-also"></a>Zobacz także

- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Analizowanie naruszeń zasady progu](../test/analyze-threshold-rule-violations-in-load-tests.md)