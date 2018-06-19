---
title: Ustawienia uruchomienia testu obciążenia programu Visual Studio z wiersza polecenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, command line
- load tests, run settings, selecting
ms.assetid: 175d1d58-f09a-4449-b132-a29a394a7c8e
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 40186bde515c95638ae0bdd90b9cace92b8da4a5
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31965391"
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