---
title: Czasy reakcji testy obciążeniowe w programie Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, think times
- load tests, adding delays
- load tests, changing think times
ms.assetid: 8e03bee5-ab7b-4b40-9497-9dbe91ccb90e
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 4eafd4e031188e62b502dc7fd6c04ebee0d145d3
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/19/2018
ms.locfileid: "39153481"
---
# <a name="edit-think-times-to-simulate-website-human-interaction-delays-in-load-tests-scenarios"></a>Edytowanie czasów reakcji w celu symulowania opóźnienia interakcja z witryny sieci Web w scenariuszach testów obciążenia

Czasy reakcji służą do symulowania zachowań ludzkich, który powoduje, że osoby do interakcji z witryną sieci Web. Czasy reakcji występują między żądaniami w teście wydajności sieci Web i między poszczególnymi iteracjami testu w scenariuszu testu obciążenia. Użycie czasów reakcji w teście obciążeniowym może być przydatne przy tworzeniu bardziej dokładnych symulacji obciążenia. Można zmienić, czy testy reakcji, czasy są używane, lub zignorować obciążenia. Możesz określić, czy reakcji, czasy są używane w obciążenia testy w **edytorze testu obciążeniowego**.

 *Profil reakcji* to ustawienie ma zastosowanie do scenariusza w teście obciążeniowym. Ustawienie określa, czy reakcji, czasy, które są zapisywane w poszczególnych testów wydajności sieci Web są używane podczas testu obciążeniowego. Jeśli chcesz używać traktować razy w niektórych testów wydajności sieci Web, ale nie w innych, należy umieścić je w różnych scenariuszach. Aby uzyskać więcej informacji na temat scenariuszy, zobacz [scenariusze testów obciążenia edycji](../test/edit-load-test-scenarios.md).

 Początkowo ustawić czy używać czasów reakcji w testach obciążenia, podczas tworzenia testu obciążenia za pomocą **Kreatora nowego testu obciążeniowego**. Aby uzyskać więcej informacji, zobacz [scenariusze testów obciążenia edycji](../test/edit-load-test-scenarios.md).

 **Profil reakcji** opcje są opisane na poniższej liście:

**Off**

Czasy reakcji są ignorowane. Użyj tego ustawienia, jeśli chcesz wygenerować maksymalnego obciążenia intensywnie podkreślanie serwera sieci Web. Nie jest używana podczas próby tworzenia bardziej realistycznego interakcji użytkownika z serwerem sieci Web.

**On**

Czasy reakcji służą dokładnie tak, jak są one rejestrowane w teście wydajności sieci Web. Symuluje wielu użytkownikom uruchamianie testów wydajności sieci Web, dokładnie tak, jak zarejestrowany. Ponieważ zasymulowano obciążenie wielu użytkowników, korzystając z tych samych zdaniem czasu można utworzyć wzorzec obciążenia nienaturalnym synchronizowanych użytkowników wirtualnych.

**Rozkład normalny**

Czasy reakcji są używane, ale zróżnicowane na typową krzywą. Zapewnia bardziej realistyczna symulacja użytkowników wirtualnych przez zróżnicowanie nieco czas namysłu między żądaniami.

> [!NOTE]
> Aby uzyskać pełną listę właściwości scenariusza testów obciążenia wraz z opisami, zobacz [właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md).

## <a name="change-the-think-profile"></a>Zmień profil reakcji

### <a name="to-change-a-think-profile-in-a-load-test-scenario"></a>Aby zmienić profil reakcji w scenariuszu testu obciążenia

1.  Od wydajności sieci Web i obciążenia projektu testowego, otwórz test obciążenia.

2.  W **edytora testu obciążenia**, wybierz węzeł scenariusz, w której chcesz zmienić **profil reakcji**. **Profil reakcji** jest wyświetlany w **właściwości** okna. Naciśnij klawisz **F4** do wyświetlenia **właściwości** okna.

3.  Zmiana **profil reakcji** właściwość **właściwości** okna.

4.  Po zmianie właściwości, wybierz **Zapisz** na **pliku** menu. Następnie można uruchomić test obciążenia przy użyciu nowego profilu reakcji.

## <a name="see-also"></a>Zobacz także

- [Edytowanie scenariuszy testu obciążenia](../test/edit-load-test-scenarios.md)