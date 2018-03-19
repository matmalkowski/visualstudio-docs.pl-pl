---
title: "Ustawienia uruchomienia testu obciążenia programu Visual Studio z wiersza polecenia | Dokumentacja firmy Microsoft"
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- load tests, command line
- load tests, run settings, selecting
ms.assetid: 175d1d58-f09a-4449-b132-a29a394a7c8e
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: e7a9a7dec6fffdb51cf71ff5a45a2841c616f8c0
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-select-a-load-test-run-setting-to-use-from-the-command-line"></a>Porady: wybieranie ustawień testów obciążenia do zastosowania z wiersza polecenia

Testu obciążenia może zawierać jeden lub więcej *parametrów uruchomieniowych*, które są zestaw właściwości wpływające na uruchomień testów obciążenia. Parametry uruchomieniowe są pogrupowane według kategorii w oknie właściwości. Po uruchomieniu testu obciążenia używa parametr uruchomieniowy, który jest aktualnie ustawione jako aktywne.

 Jeśli test obciążenia zawiera tylko jeden uruchomieniowy, zawsze jest aktywnym węźle. Jeśli test obciążenia zawiera wiele parametrów uruchomieniowych węzłów, można wybrać jeden do użycia podczas testu obciążenia z wiersza polecenia. Zobacz [porady: Dodawanie dodatkowych ustawień dla testu obciążenia](../test/how-to-add-additional-run-settings-to-a-load-test.md).

## <a name="to-change-the-run-setting-from-the-command-line"></a>Aby zmienić ustawienie Uruchom z wiersza polecenia

1.  Jeśli chcesz używać różnych ustawień wykonywania w wierszu polecenia przeprowadzać strategii parametru kontekstu, użyj następującego polecenia:

    `Set Test.UseRunSetting= CorporateStagingWebServer`

2.  Uruchamianie testu obciążenia przy użyciu przełącznika mstest:

    `mstest /testcontainer:loadtest1.loadtest`

## <a name="see-also"></a>Zobacz także

- [Konfigurowanie ustawień testu obciążenia](../test/configure-load-test-run-settings.md)
- [Określanie zbiorów liczników oraz zasad progu dla komputerów w teście obciążenia](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Porady: Dodawanie dodatkowych ustawień dla testu obciążenia](../test/how-to-add-additional-run-settings-to-a-load-test.md)
- [Porady: Wybieranie ustawień aktywnych dla testu obciążenia](../test/how-to-select-the-active-run-setting-for-a-load-test.md)