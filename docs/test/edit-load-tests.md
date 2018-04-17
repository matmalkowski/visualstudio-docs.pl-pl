---
title: Edycja testów obciążenia w programie Visual Studio | Dokumentacja firmy Microsoft
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Load Test Editor
- load tests, Load Test Editor
ms.assetid: ba16ed02-137e-40bf-a4cb-45d87d922d37
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 6e79dd964593e79c69ec6ec8ab44f10ff4c9ca99
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="edit-load-tests"></a>Edytuj testów obciążenia

Testy obciążenia Uruchamianie testów wydajności sieci Web i testów jednostkowych, aby symulować wielu użytkowników jednocześnie dostęp do serwera. Test obciążeniowy umożliwia dostęp do danych obciążeniowych i wydajnościowych aplikacji. Test obciążeniowy można skonfigurować tak, aby emulował różne warunki obciążenia, np. obciążenie przez użytkowników i typy sieci.

> [!NOTE]
> Testów obciążenia jest dostępna tylko w wersji Enterprise programu Visual Studio 2017 r.

Test obciążenia jest definiowana za pomocą *scenariusze*, *licznika zestawy*, i *parametrów uruchomieniowych*. Poniższa ilustracja wyjaśniono różnice między [scenariusze](../test/edit-load-test-scenarios.md), [licznika zestawy](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md), i [parametrów uruchomieniowych](../test/load-test-run-settings-properties.md):

![Architektura testu obciążenia](../test/media/load_test_editor.png)

## <a name="edit-load-test-scenario-settings"></a>Edytuj ustawienia scenariusza testu obciążenia

Scenariusz jest używana do modelu, jak grupa użytkowników współdziała z aplikacji serwera. Scenariusz składa się z wzorca obciążenia, modelu testu mieszanego, testu mieszanego, mieszanej przeglądarki i mieszanego profilu sieciowego. Test obciążeniowy może mieć więcej niż jeden scenariusz, a jeden scenariusz może zawierać testy wydajności sieci Web oraz testy jednostkowe. Grupując podobne ustawienia, scenariusz umożliwia łączenie i wspólne wykonywanie testów o podobnym charakterze.

Aby uzyskać więcej informacji, zobacz [edytowanie scenariuszy testu obciążenia](../test/edit-load-test-scenarios.md) i [właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md).

## <a name="configure-and-manage-performance-counter-sets"></a>Konfigurowanie i zarządzanie zbiorami liczników wydajności

Testy obciążenia udostępniają zbiorów liczników o nazwie, uporządkowane według technologii, które są przydatne podczas analizowania danych licznika wydajności. Zestawy liczników obejmują testu obciążenia, usługi IIS, platformy ASP.NET i SQL. Po utworzeniu testu obciążenia przy użyciu nowego załadować Test kreatora początkowego zestawu liczników wstępnie zdefiniowane i ważne jest skonfigurowany dla komputerów, które określają do uwzględnienia w teście obciążenia. Możesz zarządzać liczniki w edytorze testu obciążenia.

Aby uzyskać więcej informacji, zobacz [Określanie zbiorów liczników oraz zasad progu dla komputerów w teście obciążenia](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

## <a name="configure-and-manage-load-test-run-settings"></a>Konfigurowanie i zarządzanie nimi ustawień uruchomienia testu obciążenia

Ustawienia uruchamiania są właściwości wpływające na uruchomieniu testu obciążenia. Parametry uruchomieniowe są pogrupowane według kategorii w oknie właściwości.

Aby uzyskać więcej informacji, zobacz [Konfigurowanie ustawień uruchomienia testu obciążenia](../test/configure-load-test-run-settings.md) i [właściwości ustawień uruchamiania testu obciążenia](../test/load-test-run-settings-properties.md).

## <a name="see-also"></a>Zobacz także

- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Analizowanie naruszeń zasady progu](../test/analyze-threshold-rule-violations-in-load-tests.md)