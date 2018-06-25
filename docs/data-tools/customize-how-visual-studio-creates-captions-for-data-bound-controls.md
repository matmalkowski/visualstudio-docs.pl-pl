---
title: Dostosowywanie sposobu tworzenia podpisów dla kontrolek powiązanych z danymi przez program Visual Studio
ms.date: 11/03/2017
ms.topic: conceptual
helpviewer_keywords:
- Label captions, Data Sources window
- smart captions
- captions, data-bound
- Data Sources Window, label captions
ms.assetid: 6d4d15f8-4d78-42fd-af64-779ae98d62c8
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 69e97efe6db8b06f476b7dc004e3b52a77701cb0
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36758423"
---
# <a name="customize-how-visual-studio-creates-captions-for-data-bound-controls"></a>Dostosowywanie sposobu tworzenia podpisów dla kontrolek powiązanych z danymi przez program Visual Studio

Gdy przeciągnij elementy z [Data Sources — okno](add-new-data-sources.md) do konstruktora, szczególną uwagę wejścia play: nazwy kolumn w etykietach podpis są ponownie sformatowany na ciąg był bardziej czytelny, gdy dwie lub więcej wyrazów okaże się, że połączone ze sobą. Można dostosować sposób tworzenia etykiety, ustawiając **SmartCaptionExpression**, **SmartCaptionReplacement**, i **SmartCaptionSuffix** wartości w **projektantów HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Data** klucza rejestru.

> [!NOTE]
> Ten klucz rejestru nie istnieje, dopóki nie zostaną utworzone.

Podpisy inteligentne jest kontrolowany przez wyrażenie regularne, wprowadzany do wartości **SmartCaptionExpression** wartości. Dodawanie **projektanci danych** Określa podpis etykiety domyślne wyrażenie regularne przesłania klucza rejestru. Aby uzyskać więcej informacji na temat wyrażeń regularnych, zobacz [za pomocą wyrażeń regularnych w programie Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

W poniższej tabeli opisano wartości rejestru, które sterują podpis etykiety.

|Element rejestru|Opis|
|-------------------|-----------------|
|**SmartCaptionExpression**|Wyrażenie regularne, używanej do dopasowania Twoich wzorców.|
|**SmartCaptionReplacement**|Format wyświetlania grup dopasowywane w **SmartCaptionExpression**.|
|**SmartCaptionSuffix**|Opcjonalny ciąg do dołączenia do końca podpis.|

W poniższej tabeli wymieniono wewnętrzny domyślne ustawienia tych wartości rejestru.

|Element rejestru|Wartość domyślna|Wyjaśnienie|
|-------------------|-------------------|-----------------|
|**SmartCaptionExpression**|**(\\\p{Ll}) (\\\p{Lu})&#124;_ +**|Dopasowuje małą literę, a następnie wielkie litery lub znaku podkreślenia.|
|**SmartCaptionReplacement**|**$1 $2**|**$1** reprezentuje wszystkie znaki dopasowana w pierwszym nawiasów wyrażenia i **$2** reprezentuje znaków dopasowywane w nawiasach drugiego. Zastąpienie jest pierwsze dopasowanie, spacji i drugi dopasowania.|
|**SmartCaptionSuffix**|**:**|Reprezentuje znak dołączany do zwracany ciąg. Na przykład, jeśli podpis jest `Company Name`, sufiks ułatwia `Company Name:`|

> [!CAUTION]
> Należy zachować ostrożność w Edytorze rejestru żadnego działania. Utwórz kopię zapasową rejestru przed rozpoczęciem edycji. Jeśli korzystanie z Edytora rejestru może spowodować poważne problemy, które może być konieczna ponowna instalacja systemu operacyjnego. Microsoft nie gwarantuje, że można rozwiązać problemy powodujące przez niewłaściwego używania Edytora rejestru. Używasz Edytora rejestru na własne ryzyko.
>
> Instrukcje dotyczące tworzenia kopii zapasowej, edytowanie i przywracanie rejestru zawiera następujący artykuł bazy wiedzy: [Opis rejestru systemu Microsoft Windows](http://support.microsoft.com/default.aspx?scid=kb;en-us;256986) (http://support.microsoft.com/default.aspx?scid=kb; en-us; 256986)

## <a name="modify-the-smart-captioning-behavior-of-the-data-sources-window"></a>Modyfikowanie inteligentne podpisów okna źródeł danych

1.  Otwórz okno polecenia, klikając przycisk **Start** , a następnie **Uruchom**.

2.  Typ `regedit` w **Uruchom** okno dialogowe, a następnie kliknij przycisk **OK**.

3.  Rozwiń węzeł **HKEY_CURRENT_USER** > **oprogramowania** > **Microsoft** > **VisualStudio**węzła.

7.  Kliknij prawym przyciskiem myszy **15.0** węzeł i utworzyć nową **klucza** o nazwie `Data Designers`.

8.  Kliknij prawym przyciskiem myszy **projektanci danych** węzeł i Utwórz trzy nowe wartości ciągu:

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`

11. Kliknij prawym przyciskiem myszy **SmartCaptionExpression** wartość, a następnie wybierz **Modyfikuj**.

12. Wprowadź wyrażenie regularne mają **źródeł danych** okno, aby użyć.

13. Kliknij prawym przyciskiem myszy **SmartCaptionReplacement** wartość, a następnie wybierz **Modyfikuj**.

14. Zastąpienia wprowadź ciąg sformatowany w sposób wyświetlić wzorce dopasowywane w wyrażeniu regularnym.

15. Kliknij prawym przyciskiem myszy **SmartCaptionSuffix** wartość, a następnie wybierz **Modyfikuj**.

16. Wprowadź wszystkie znaki, które mają być wyświetlane na końcu podpis.

    Przy następnym przeciągnij elementy z **źródeł danych** , etykiety podpis są tworzone przy użyciu nowej wartości rejestru, pod warunkiem.

## <a name="turn-off-the-smart-captioning-feature"></a>Wyłącz funkcję podpisów inteligentne

1.  Otwórz okno polecenia, klikając przycisk **Start** , a następnie **Uruchom**.

2.  Typ `regedit` w **Uruchom** okno dialogowe, a następnie kliknij przycisk **OK**.

3.  Rozwiń węzeł **HKEY_CURRENT_USER** > **oprogramowania** > **Microsoft** > **VisualStudio**węzła.

7.  Kliknij prawym przyciskiem myszy **15.0** węzeł i utworzyć nową **klucza** o nazwie `Data Designers`.

8.  Kliknij prawym przyciskiem myszy **projektanci danych** węzeł i Utwórz trzy nowe wartości ciągu:

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`

11. Kliknij prawym przyciskiem myszy **SmartCaptionExpression** elementu, a następnie wybierz **Modyfikuj**.

12. Wprowadź `(.*)` dla wartości. Jest to zgodny cały ciąg.

13. Kliknij prawym przyciskiem myszy **SmartCaptionReplacement** elementu, a następnie wybierz **Modyfikuj**.

14. Wprowadź `$1` dla wartości. Spowoduje to zastąpienie ciąg o pasujących wartości jest cały ciąg, dzięki czemu pozostanie bez zmian.

    Przy następnym przeciągnij elementy z **źródeł danych** okna, etykiety podpis są tworzone za pomocą podpisów bez modyfikacji.

## <a name="see-also"></a>Zobacz także

- [Powiązywanie formantów z danymi w Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)