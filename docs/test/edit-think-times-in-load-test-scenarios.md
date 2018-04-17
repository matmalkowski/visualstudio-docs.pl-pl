---
title: Czasów reakcji obciążenia testowania w programie Visual Studio | Dokumentacja firmy Microsoft
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
ms.technology: vs-ide-test
ms.openlocfilehash: e67e514b3b977e50be553704ec1997ce7476f045
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="edit-think-times-to-simulate-website-human-interaction-delays-in-load-tests-scenarios"></a>Edytowanie czasów reakcji w celu symulowania opóźnienia człowieka witryny sieci Web w scenariuszach testów obciążenia

Czasów reakcji są używane do symulowania człowieka zachowanie, które powoduje, że osoby między interakcji z witryną sieci Web. Czasów reakcji wystąpić żądań w teście wydajności sieci Web oraz między iteracji testowych w scenariuszu testu obciążenia. Może być przydatne podczas tworzenia bardziej dokładne symulacje obciążenia przy użyciu czasów reakcji w teście obciążenia. Czy testy Pomyśl czasy są używane lub ignorowane w obciążeniu, można zmienić. Możesz określić, czy Pomyśl czasy są używane w obciążenia testów w edytorze testu obciążenia.

 *Wziąć pod uwagę profilu* to ustawienie ma zastosowanie do scenariusza w teście obciążenia. Ustawienie określa, czy traktować razy, które są zapisywane w poszczególnych testów wydajności sieci Web są używane podczas testu obciążenia. Jeśli chcesz użyć wziąć pod uwagę razy w niektórych testów wydajności sieci Web, ale nie w innych osób, należy umieścić je w różnych scenariuszach. Aby uzyskać więcej informacji na temat scenariuszy, zobacz [edytowanie scenariuszy testu obciążenia](../test/edit-load-test-scenarios.md).

 Początkowo ustawiony czy używać czasów reakcji w testach obciążenia podczas tworzenia testu obciążenia za pomocą załadować Test Kreator nowego. Aby uzyskać więcej informacji, zobacz [edytowanie scenariuszy testu obciążenia](../test/edit-load-test-scenarios.md).

 Na poniższej liście opisano opcje profilu wziąć pod uwagę:

**Off**

Czasy reakcji są ignorowane. Tego ustawienia należy używać wtedy, gdy chcesz wygenerować maksymalne obciążenie w dużym stopniu obciąża aspekt serwera sieci Web. Nie jest używana podczas próby utworzenia bardziej realistyczne interakcji użytkowników z serwera sieci Web.

**On**

Czasy reakcji są używane, dokładnie tak, jak są one rejestrowane w teście wydajności sieci Web. Symuluje wielu użytkownikom uruchamianie testów wydajności sieci Web, dokładnie tak, jak rejestrowane. Ponieważ symuluje testu obciążenia wielu użytkowników, korzystającej z tego samego wydaje się, że czas można utworzyć wzorca obciążenia nienaturalnej zsynchronizowanych użytkowników wirtualnych.

**Rozkład normalny**

Czasów reakcji są używane, ale różne na typową krzywą. Zapewnia bardziej realistyczne symulacji wirtualnych użytkowników przez zróżnicowanie nieco czasu namysłu między żądaniami.

> [!NOTE]
> Aby uzyskać pełną listę właściwości scenariusza testów obciążenia i ich opisy, zobacz [właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md).

## <a name="changing-the-think-profile"></a>Zmiana reakcji profilu

### <a name="to-change-a-think-profile-in-a-load-test-scenario"></a>Aby zmienić reakcji profil w scenariuszu testu obciążenia

1.  Od wydajności sieci Web i obciążenia projekt testowy, otwórz testu obciążenia.

2.  W **edytora testu obciążenia**, wybierz węzeł scenariusz, której chcesz zmienić **wziąć pod uwagę profilu**. **Wziąć pod uwagę profilu** jest wyświetlany w oknie właściwości. Naciśnij klawisz F4, aby wyświetlić okno właściwości.

3.  Zmień **wziąć pod uwagę profilu** właściwości w oknie właściwości.

4.  Po zmianie właściwości, wybierz **zapisać** na **pliku** menu. Następnie możesz uruchomić test obciążenia za pomocą nowego profilu reakcji.

## <a name="see-also"></a>Zobacz także

- [Edytowanie scenariuszy testu obciążenia](../test/edit-load-test-scenarios.md)