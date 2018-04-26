---
title: 'Porady: tworzenie i modyfikacja poziomów MIP'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: f64d4369-2307-4175-a39a-2e45506f7fa1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5b2948b33db198ddd8f7e002acbad155da66da58
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-and-modify-mip-levels"></a>Porady: tworzenie i modyfikacja poziomów MIP
W tym dokumencie przedstawiono sposób użycia **edytor obrazów** do generowania i zmodyfikować *poziomów Mipmapy* dla przestrzeni tekstury elementu szczegóły na poziomie (LoD).

## <a name="generating-mip-levels"></a>Generowanie poziomów Mipmapy
 *Mipmapowaniem* to technika, używany do renderowania przyspieszy i zmniejszyć artefakty aliasów na obiektach teksturą przez wstępnie Obliczanie i przechowywanie kopii kilka tekstury w różnych rozmiarach. Każdej kopii, która nazywa się poziom Mipmapy, jest połowa szerokości i wysokości poprzedniej kopii. Po wyrenderowaniu tekstury na powierzchni obiektu poziom Mipmapy, który najlepiej odpowiada miejsca na ekranie obszaru powierzchni teksturą zostanie automatycznie wybrany. Oznacza to, czy sprzęt graficzny nie ma do filtrowania tekstury zbyt duży do zachowania spójności jakości visual. Mimo że pamięci koszt przechowywania poziomów Mipmapy to około 33% więcej niż w przypadku oryginalnego tekstury samodzielnie, wydajności i jakości obrazu zyski justify go.

#### <a name="to-generate-mip-levels"></a>Aby wygenerować poziomów Mipmapy

1.  Zaczynać tekstury podstawowe, zgodnie z opisem w [porady: Tworzenie podstawowego tekstury](../designers/how-to-create-a-basic-texture.md). Aby uzyskać najlepsze rezultaty, należy określić tekstury, szerokość i wysokość, który jest potęgą liczby dwa rozmiaru, na przykład 256, 512, 1024 i tak dalej.

2.  Generowanie poziomów Mipmapy. Na **tryb edytora obrazów** narzędzi wybierz **zaawansowane**, **narzędzia**, **Generowanie Mips**.

     Zwróć uwagę, że **przejdź do następnego poziomu mipmapy** i **przejdź do poprzedniego poziom mipmapy** przyciski będą teraz wyświetlane na **tryb edytora obrazów** paska narzędzi. Jeśli **właściwości** okno jest wyświetlane, należy także zauważyć, że właściwości tylko do odczytu **poziom mipmapy** i **liczba poziom mipmapy** teraz wyświetlane we właściwościach obrazu.

## <a name="modifying-mip-levels"></a>Modyfikowanie poziomów Mipmapy
 Aby osiągnąć efekty specjalne lub zwiększyć jakość obrazu na określonym poziomie szczegółowości, można zmodyfikować każdy poziom Mipmapy indywidualnie. Na przykład można nadać teksturą obiektu wyglądać inaczej w odległości (większej odległości odpowiada mniejszych poziomów Mipmapy) lub może upewnij się, że tekstury, które zawierają tekst lub symbole one czytelne nawet na mniejsze poziomów Mipmapy.

#### <a name="to-modify-an-individual-mip-level"></a>Aby zmodyfikować poszczególne poziom Mipmapy

1.  Wybierz poziom Mipmapy, który chcesz zmodyfikować. Na **tryb edytora obrazów** narzędzi, użyj **przejdź do następnego poziomu Mipmapy** i **przejdź do poprzedniego poziom Mipmapy** przycisków, aby przechodzić między poziomów Mipmapy.

2.  Po wybraniu poziom Mipmapy, który chcesz zmodyfikować, korzystając narzędzi do rysowania można go zmodyfikować bez zmiany zawartości z innych poziomów Mipmapy. Narzędzia do rysowania są dostępne na **edytor obrazów** paska narzędzi. Po wybraniu narzędzia, można zmienić jego właściwości w **właściwości** okna. Aby uzyskać informacje dotyczące narzędzi do rysowania i ich właściwości, zobacz [edytor obrazów](../designers/image-editor.md).

> [!NOTE]
>  Jeśli nie ma potrzeby modyfikowania zawartość poszczególnych poziomów Mipmapy — jak może osiągnąć niektórych skutków — zaleca się generowanie mipmapy z tekstury źródło w czasie kompilacji. Pomaga to zapewnić, że poziomów Mipmapy pozostają zsynchronizowane z tekstury źródła, ponieważ modyfikacje poziom Mipmapy nie są przenoszone na innych poziomach automatycznie. Aby uzyskać więcej informacji na temat generowania mipmapy w czasie kompilacji, zobacz [porady: eksportowanie tekstury tego mipmapy zawiera](../designers/how-to-export-a-texture-that-contains-mipmaps.md).

## <a name="see-also"></a>Zobacz także

- [Instrukcje: tworzenie tekstury podstawowej](../designers/how-to-create-a-basic-texture.md)