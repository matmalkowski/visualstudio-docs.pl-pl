---
title: Wybieranie ustawień dla testu obciążenia w programie Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, run settings, active
ms.assetid: ed6ff546-acfa-4dd8-b3a2-6e7455930ca4
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 8566964ab8dd3fbfa1fca15ce8362218c99c27e6
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-select-the-active-run-setting-for-a-load-test"></a>Porady: wybieranie ustawień aktywnych dla testu obciążenia

Po utworzeniu testu obciążenia z **załadować Test Kreatora nowego**, można użyć **edytorze testu obciążenia** Aby zmienić właściwości scenariuszy, aby spełnić potrzeby testowania i cele.

Test obciążenia może zawierać jeden lub więcej *parametrów uruchomieniowych* będące zestaw właściwości wpływające na uruchomień testów obciążenia. Parametry uruchomieniowe są pogrupowane według kategorii w oknie właściwości. Po uruchomieniu testu obciążenia używa parametr uruchomieniowy, który jest aktualnie ustawione jako aktywne.

> [!NOTE]
> Aby uzyskać pełną listę właściwości parametry uruchomieniowe i ich opisy, zobacz [właściwości ustawień uruchamiania testu obciążenia](../test/load-test-run-settings-properties.md).

Jeśli test obciążenia zawiera tylko jeden węzeł ustawień w obszarze **parametrów uruchomieniowych** folderu, w tym węźle jest zawsze aktywnego węzła. Jeśli test obciążenia zawiera wiele parametrów uruchomieniowych węzłów, można wybrać jeden do użycia podczas uruchamiania testu obciążenia. Zobacz [porady: Dodawanie dodatkowych ustawień dla testu obciążenia](../test/how-to-add-additional-run-settings-to-a-load-test.md).

W edytorze testu obciążenia, aktywnego ustawienia uruchamiania jest identyfikowany przez sufiks "[Active]".

## <a name="selecting-the-active-run-setting"></a>Wybieranie ustawień aktywnych

### <a name="to-select-the-active-run-setting-in-a-load-test"></a>Aby wybrać aktywnych ustawieniach testu w teście obciążenia

1.  Otwórz testu obciążenia.

2.  Rozwiń węzeł **parametrów uruchomieniowych** folderu.

3.  Kliknij prawym przyciskiem myszy węzeł uruchomieniowych, który ma być aktywnym węźle, a następnie wybierz pozycję **Ustaw jako aktywny**.

     W **Edito testu obciążenia**r, węzeł odpowiednich ustawień jest aktualizowane wraz z sufiksem "[Active]".

     Ustawienia uruchamiania wybranego staje się aktywny, a pozostaje aktywne, dopóki nie wybierzesz inną Uruchom ustawienie jako aktywne.

> [!NOTE]
> Można zastąpić, uruchom active ustawienie przez ustawienie zmiennej środowiskowej o nazwie `Test.UseRunSetting=<run setting name>`. Jest to przydatne, gdy Uruchamianie testu obciążenia z wiersza polecenia lub pliku wsadowego. Dzięki temu można określić różne ustawienia wykonywania bez konieczności otwierania testu obciążenia.


## <a name="specifying-the-run-setting-to-use-from-the-command-line"></a>Określenie parametru uruchomieniowego do użycia z poziomu wiersza polecenia
 Można zastąpić domyślnych parametrów uruchomieniowych w teście obciążenia sieci przez ustawienie zmiennej środowiskowej w wierszu polecenia:

 **Ustaw Test.UseRunSetting=PreProdEnvironment**

 I uruchomienia testu:

 **mstest /testcontainer:loadtest1.loadtest**

## <a name="see-also"></a>Zobacz także

- [Konfigurowanie ustawień testu obciążenia](../test/configure-load-test-run-settings.md)
- [Określanie zbiorów liczników oraz zasad progu dla komputerów w teście obciążenia](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Porady: Dodawanie dodatkowych ustawień dla testu obciążenia](../test/how-to-add-additional-run-settings-to-a-load-test.md)