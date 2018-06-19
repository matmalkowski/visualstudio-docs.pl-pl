---
title: Określanie liczby iteracji testowych w ustawieniach uruchamiania testów obciążenia w programie Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, properties
- load tests, run settings
ms.assetid: 45a625db-b3e7-4d64-beda-b9a76248096d
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: ec11561a3ebe084517d1a30266f9caa6491544a7
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31965565"
---
# <a name="how-to-specify-the-number-of-test-iterations-in-a-load-test-run-setting"></a>Porady: określanie liczby iteracji testowych w ustawieniach testu obciążenia

Po utworzeniu testu obciążenia z **załadować Test Kreatora nowego**, można użyć **edytorze testu obciążenia** Aby zmienić właściwości scenariuszy, aby spełnić potrzeby testowania i cele. Aby uzyskać więcej informacji, zobacz [wskazówki: tworzenie i uruchamianie testu obciążenia](../test/walkthrough-create-and-run-a-load-test.md).

Przy użyciu **edytora testu obciążenia**, można edytować **iteracjami testu** właściwości wartości ustawień uruchamiania w oknie właściwości. **Iteracje testu** właściwość określa liczbę iteracji, aby uruchomić na wszystkich testów sieci Web wydajności i jednostka we wszystkich scenariuszach testów obciążenia przy użyciu **edytorze testu obciążenia**.

> [!NOTE]
> Aby uzyskać pełną listę właściwości parametry uruchomieniowe i ich opisy, zobacz [właściwości ustawień uruchamiania testu obciążenia](../test/load-test-run-settings-properties.md).


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