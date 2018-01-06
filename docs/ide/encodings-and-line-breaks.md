---
title: "Visual Studio, kodowanie i wiersz znaków podziału | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.Encoding
helpviewer_keywords:
- line breaks
- encoding
- Visual Studio, encoding
- editors, line breaks
- line break characters
- Visual Studio, line break characters
ms.assetid: 8f9b3ffc-7b8d-44f4-87cb-dc29105be12d
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8a472a09a4d4d67f59d7879d03b466932d1445e6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="encodings-and-line-breaks"></a>Kodowania i linie podziału
Następujące znaki będą interpretowane jako podziały wierszy w programie Visual Studio:  
  
-   CR LF: Powrotu karetki + wiersz źródła danych, 000 D + 000A znaki Unicode  
  
-   LF: Wysuwu wiersza, znaków Unicode 000A  
  
-   Ustaw: Następnego wiersza, znaków Unicode 0085  
  
-   LS: Linii separatora, znaków Unicode 2028  
  
-   PS: Separator akapitu, znaków Unicode 2029  
  
Tekst, który jest skopiowany z innych aplikacji zachowuje oryginalne kodowanie i znaki podziału wiersza. Na przykład gdy skopiować tekst ze Schowka i wklej go do pliku tekstowego w programie Visual Studio, tekst ma tych samych ustawień, które miało w Notatniku.  
  
Po otwarciu pliku, który zawiera znaki końca wiersza różnych może Zobacz okno dialogowe z pytaniem, czy znaki podziału wiersza niespójne należy znormalizować, jakiego typu wiersz podziały i wybrać.

Można użyć **pliku**, **zaawansowane opcje zapisywania** okno dialogowe, aby określić typ ma znaki końca wiersza. Możesz również zmienić kodowanie pliku z tymi samymi ustawieniami.

![Okno dialogowe Zaawansowane opcje zapisywania](media/line_endings.png)
  
> [!NOTE]
>  Jeśli nie widzisz **zaawansowane opcje zapisywania** na **pliku** menu, można go dodać. Wybierz **narzędzia**, **dostosować...** , a następnie wybierz pozycję **polecenia** kartę. W **paska Menu** listy rozwijanej wybierz pozycję **pliku**, a następnie wybierz **polecenia Dodaj...**  przycisku. W **polecenia Add** okna dialogowego, w obszarze **kategorii**, wybierz **pliku**, a następnie w **polecenia** wybierz  **Zaawansowane opcje zapisywania...** . Wybierz **OK** , a następnie wybierz **Przenieś w dół** przycisk, aby przenieść polecenie na dowolne miejsce w menu. Wybierz **zamknąć** zamknąć **Dostosuj** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Dostosowywanie menu i pasków zadań](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#customizing_menu).

Alternatywnie można uzyskać dostęp **zaawansowane opcje zapisywania** okno dialogowe, wybierając **pliku**, **zapisać \<pliku\> jako...** . W **Zapisz plik jako** oknie dialogowym Wybierz trójkąt listy rozwijanej obok pola **zapisać** przycisk i wybierz polecenie **Zapisz z kodowaniem...** .

## <a name="see-also"></a>Zobacz także
[Pisanie kodu w edytorze](../ide/writing-code-in-the-code-and-text-editor.md)