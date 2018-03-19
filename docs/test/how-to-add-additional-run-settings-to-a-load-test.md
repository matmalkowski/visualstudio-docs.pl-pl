---
title: "Dodaj parametry uruchomieniowe do testu obciążenia w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- load tests, run settings, adding
- load tests, run settings
ms.assetid: 257d2a24-d582-4cfe-8b2b-51f51ba9cc84
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: d93349f022a68b7f11367dcd775776d6f0cb32c8
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-add-additional-run-settings-to-a-load-test"></a>Porady: dodawanie dodatkowych ustawień dla testu obciążenia

Parametry uruchomieniowe testu obciążeniowego decydują o różnych innych ustawieniach. Należą do nich ustawienia czasu trwania testu, poziomu szczegółowości zbierania wyników oraz zbiorów liczników, z których dane mają być zbierane podczas przebiegów testowych. Dla każdego testu obciążeniowego można utworzyć i zapisać wiele parametrów uruchomieniowych, a następnie wybrać jedno konkretne ustawienie do użycia podczas wykonywania testu. Początkowy parametr uruchomieniowy dodaje się do testu obciążeniowego podczas tworzenia testu za pomocą Kreatora nowego testu obciążeniowego.

 Do testu obciążeniowego można dodać więcej parametrów uruchomieniowych z różnymi ustawieniami właściwości, co pozwoli wykonywać te testy w różnych warunkach. Na przykład można dodać nowe ustawienie testu określające inną częstotliwość próbkowania albo dłuższy czas trwania. W danej sesji można używać tylko jednego parametru uruchomieniowego. Przed rozpoczęciem testu należy go też wskazać jako aktywny.

## <a name="to-add-another-run-setting"></a>Aby dodać kolejny parametr uruchomieniowy

1.  Otwórz testu obciążenia.

2.  (Opcjonalnie) Rozwiń węzeł **parametrów uruchomieniowych** folderu.

3.  Kliknij prawym przyciskiem myszy **parametrów uruchomieniowych** i wybierz polecenie **dodać parametrów uruchomieniowych**.

     Nowe ustawienie uruchamiania jest dodawany do **parametrów uruchomieniowych** folderu.

4.  Na **widoku** menu, wybierz **okna właściwości**.

     Zostanie wyświetlone okno Właściwości z właściwościami dotyczącymi wybranego parametru uruchomieniowego.

5.  W oknie właściwości, użyj pola tekstowego do **nazwa** właściwość umożliwiają uruchomienie nowej Nazwa ustawienia opisuje celem parametru uruchomieniowego (na przykład **Ustawienie Uruchom: pięciominutowym Uruchom**).

6.  W oknie Właściwości zmodyfikuj parametry uruchomieniowe. Na przykład zmienić czas trwania testu na **00:05:00** testu przez pięć minut.

    > [!NOTE]
    > Aby uzyskać pełną listę właściwości parametry uruchomieniowe i ich opisy, zobacz [właściwości ustawień uruchamiania testu obciążenia](../test/load-test-run-settings-properties.md).

     Teraz można określić, że dodany parametr uruchomieniowy ma być używany, ustawiając mu status aktywności. Aby uzyskać więcej informacji, zobacz [porady: Wybieranie aktywne ustawienie uruchamiania dla testu obciążenia](../test/how-to-select-the-active-run-setting-for-a-load-test.md).

## <a name="see-also"></a>Zobacz także

- [Konfigurowanie ustawień testu obciążenia](../test/configure-load-test-run-settings.md)
- [Określanie zbiorów liczników oraz zasad progu dla komputerów w teście obciążenia](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)