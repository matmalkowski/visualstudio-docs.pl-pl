---
title: Określ ustawienia uruchamiania liczby iteracji testowych w teście obciążenia w programie Visual Studio | Dokumentacja firmy Microsoft
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, properties
- load tests, run settings
ms.assetid: 45a625db-b3e7-4d64-beda-b9a76248096d
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 06e99eafc6089853b90dd2196fb9152e2639b32b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-specify-the-number-of-test-iterations-in-a-load-test-run-setting"></a>Porady: określanie liczby iteracji testowych w ustawieniach testu obciążenia

Po utworzeniu testu obciążenia z **załadować Test Kreatora nowego**, można użyć **edytorze testu obciążenia** Aby zmienić właściwości scenariuszy, aby spełnić potrzeby testowania i cele. Aby uzyskać więcej informacji, zobacz [wskazówki: tworzenie i uruchamianie testu obciążenia](../test/walkthrough-create-and-run-a-load-test.md).

Przy użyciu **edytora testu obciążenia**, można edytować **iteracjami testu** właściwości wartości ustawień uruchamiania w oknie właściwości. **Iteracje testu** właściwość określa liczbę iteracji, aby uruchomić na wszystkich testów sieci Web wydajności i jednostka we wszystkich scenariuszach testów obciążenia przy użyciu **edytorze testu obciążenia**.

> [!NOTE]
>  Aby uzyskać pełną listę właściwości parametry uruchomieniowe i ich opisy, zobacz [właściwości ustawień uruchamiania testu obciążenia](../test/load-test-run-settings-properties.md).

## <a name="to-specify-the-number-of-test-iterations-in-a-run-setting"></a>Umożliwia określenie liczby iteracji testowych w ustawieniach testu

1.  Otwórz testu obciążenia.

     **Edytorze testu obciążenia** zostanie wyświetlony i drzewa testu obciążenia.

2.  Obciążenia przetestować drzewa, w **parametrów uruchomieniowych** folderu, wybierz ustawienie uruchamiania.

3.  Na **widoku** menu, wybierz opcję **okna właściwości** do wyświetlania obciążenia Uruchom kategorii i właściwości tego ustawienia.

4.  Ustaw **iteracjami testu użyj** właściwości **True**.

5.  W **iteracje testu** właściwości, wprowadź liczbę wskazującą liczbę iteracji testu, aby uruchomić podczas testu obciążenia.

6.  Po zmianie właściwości, wybierz **zapisać** na **pliku** menu. Następnie możesz uruchomić test obciążenia przy użyciu nowego **iteracje testu** wartość.

## <a name="see-also"></a>Zobacz także

- [Konfigurowanie ustawień testu obciążenia](../test/configure-load-test-run-settings.md)
- [Właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md)