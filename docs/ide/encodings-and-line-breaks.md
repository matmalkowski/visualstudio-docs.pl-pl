---
title: Visual Studio, kodowanie i wiersz znaków podziału
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.Encoding
helpviewer_keywords:
- line breaks
- encoding
- Visual Studio, encoding
- editors, line breaks
- line break characters
- Visual Studio, line break characters
ms.assetid: 8f9b3ffc-7b8d-44f4-87cb-dc29105be12d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: acb96e598128060563d12809a300318ccb929aaf
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2018
---
# <a name="encodings-and-line-endings"></a>Kodowanie i wiersza zakończenia

Następujące znaki będą interpretowane jako podziały wierszy w programie Visual Studio:

- CR LF: Powrotu karetki + wiersz źródła danych, 000 D + 000A znaki Unicode

- LF: Wysuwu wiersza, znaków Unicode 000A

- Ustaw: Następnego wiersza, znaków Unicode 0085

- LS: Linii separatora, znaków Unicode 2028

- PS: Separator akapitu, znaków Unicode 2029

Tekst, który jest skopiowany z innych aplikacji zachowuje oryginalne kodowanie i znaki podziału wiersza. Na przykład gdy skopiować tekst ze Schowka i wklej go do pliku tekstowego w programie Visual Studio, tekst ma tych samych ustawień, które miało w Notatniku.

Po otwarciu pliku, który zawiera znaki końca wiersza różnych może Zobacz okno dialogowe z pytaniem, czy znaki podziału wiersza niespójne należy znormalizować, jakiego typu wiersz podziały i wybrać.

## <a name="advanced-save-options"></a>Zaawansowane opcje zapisywania

Można użyć **pliku** > **zaawansowane opcje zapisywania** okno dialogowe, aby określić typ ma znaki końca wiersza. Możesz również zmienić kodowanie pliku z tymi samymi ustawieniami.

![Okno dialogowe Zaawansowane opcje zapisywania](media/line_endings.png)

> [!NOTE]
> Jeśli nie widzisz **zaawansowane opcje zapisywania** na **pliku** menu, można go dodać. Wybierz **narzędzia**, **dostosować...** , a następnie wybierz pozycję **polecenia** kartę. W **paska Menu** listy rozwijanej wybierz pozycję **pliku**, a następnie wybierz **polecenia Dodaj...**  przycisku. W **polecenia Add** okna dialogowego, w obszarze **kategorii**, wybierz **pliku**, a następnie w **polecenia** wybierz **Zaawansowane opcje zapisywania...**. Wybierz **OK** , a następnie wybierz **Przenieś w dół** przycisk, aby przenieść polecenie na dowolne miejsce w menu. Wybierz **zamknąć** zamknąć **Dostosuj** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Dostosowywanie menu i pasków zadań](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#customizing_menu).
>
> Alternatywnie można uzyskać dostęp **zaawansowane opcje zapisywania** okno dialogowe, wybierając **pliku** > **zapisać \<pliku\> jako...** . W **Zapisz plik jako** oknie dialogowym Wybierz trójkąt listy rozwijanej obok pola **zapisać** przycisk i wybierz polecenie **Zapisz z kodowaniem...** .

## <a name="see-also"></a>Zobacz także

- [Funkcje Edytor kodu](../ide/writing-code-in-the-code-and-text-editor.md)