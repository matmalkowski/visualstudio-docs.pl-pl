---
title: Ustawienia przebiegu testu obciążenia programu Visual Studio z poziomu wiersza polecenia
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
ms.openlocfilehash: 263f8a671897b5f9c8af835f13214139e3abef17
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2018
ms.locfileid: "39382480"
---
# <a name="how-to-select-a-load-test-run-setting-to-use-from-the-command-line"></a>Porady: Wybierz ustawienie, aby korzystać z wiersza polecenia do uruchomienia testu obciążenia

Test obciążenia może obejmować *parametrów uruchomieniowych*, które są właściwościami, które mają wpływ na sposób wykonywania testu obciążeniowego. Ustawienia uruchamiania są zorganizowane według kategorii w **właściwości** okna. Po uruchomieniu testu obciążenia używa uruchomieniowy, który jest aktualnie ustawiona jako aktywna.

 Jeśli test obciążeniowy zawiera tylko jedno ustawienie uruchamiania, zawsze jest aktywnym węźle. Jeśli test obciążeniowy zawiera wiele węzłów parametrów uruchomieniowych, możesz wybrać jeden do użycia podczas uruchamiania testu obciążenia z wiersza polecenia. Zobacz [porady: Dodawanie dodatkowych parametrów uruchomieniowych do testu obciążeniowego](../test/how-to-add-additional-run-settings-to-a-load-test.md).

## <a name="to-change-the-run-setting-from-the-command-line"></a>Aby zmienić parametr uruchomieniowy, z poziomu wiersza polecenia

1.  Jeśli chcesz korzystać z zalet strategii parametru kontekstu przy użyciu różnych parametrów uruchomieniowych z wiersza polecenia, użyj następującego polecenia:

    `Set Test.UseRunSetting= CorporateStagingWebServer`

2.  Uruchom test obciążenia przy użyciu przełącznika mstest:

    `mstest /testcontainer:loadtest1.loadtest`

## <a name="see-also"></a>Zobacz także

- [Konfigurowanie ustawień testu obciążenia](../test/configure-load-test-run-settings.md)
- [Określanie zbiorów liczników oraz zasad progu dla komputerów w teście obciążeniowym](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Porady: Dodawanie dodatkowych ustawień przebiegu testu obciążenia](../test/how-to-add-additional-run-settings-to-a-load-test.md)
- [Porady: Wybierz aktywne ustawienia uruchamiania dla testu obciążenia](../test/how-to-select-the-active-run-setting-for-a-load-test.md)
