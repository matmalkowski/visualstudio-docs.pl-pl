---
title: Uruchamianie testu jednostkowego jako procesu 64-bitowe w Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- unit tests, creating
- unit tests, running
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 2b6e44ae9b0587a044cb1a8a0d62db068dfc76d6
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31966629"
---
# <a name="run-a-unit-test-as-a-64-bit-process"></a>Uruchamianie testu jednostkowego jako procesu 64-bitowego

Jeśli masz komputera 64-bitowego, można uruchomić testów jednostkowych i przechwytywanie informacji o pokryciu kodu jako proces 64-bitowy.

## <a name="to-run-a-unit-test-as-a-64-bit-process"></a>Uruchamianie testu jednostkowego jako procesu 64-bitowego

1. Jeśli Twoje kodu lub testy zostały skompilowane jako 32-bitowy/x86, ale chcesz je uruchomić jako proces 64-bitowy, skompiluj ponownie, ich jako **Any CPU**, lub opcjonalnie jako **64-bitowych**.

    > [!TIP]
    > Maksymalna elastyczność kompilacji projektów testów z **Any CPU** konfiguracji. Następnie możesz uruchomić na zarówno 32-bitowe i 64-bitowych agentów. Nie ma żadnych dodatkowych zalet kompilowanie projektów testów z **64-bitowych** konfiguracji.

2. Z menu programu Visual Studio wybierz **testu**, a następnie wybierz **ustawienia**, a następnie wybierz pozycję **architektury procesora**. Wybierz **x64** do uruchamiania testów jako procesu 64-bitowego.

   - lub -

   Określ `<TargetPlatform>x64</TargetPlatform>` w *runsettings* pliku. Zaletą tej metody jest można określić grupy ustawień w różnych plikach i szybkie przełączanie się między innymi ustawieniami. Można również skopiować ustawienia między rozwiązaniami. Aby uzyskać więcej informacji, zobacz [Konfigurowanie testów jednostkowych przy użyciu pliku runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

## <a name="see-also"></a>Zobacz także

- [Przeprowadzanie testów jednostkowych za pomocą narzędzia Eksplorator testów](../test/run-unit-tests-with-test-explorer.md)
- [Testowanie jednostek kodu](../test/unit-test-your-code.md)
