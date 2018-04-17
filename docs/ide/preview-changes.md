---
title: Podgląd zmian kodu w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 12/16/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
f1_keywords:
- vs.codefix.previewchanges
ms.workload:
- multiple
ms.openlocfilehash: cc838d55e83a5b606059acbf068639116ab012bd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="preview-changes-window"></a>Podgląd zmian okna

Korzystając z różnych *szybkie akcje* lub *Refactoring* narzędzia w programie Visual Studio, możliwe jest często podgląd zmian, które mają być dokonane do projektu przed rozpoczęciem akceptowania je. **Podgląd zmian** okno jest, gdzie jest to zrobić.  Na przykład, w tym miejscu jest **podgląd zmian** okna pokazującego, co zostanie zmieniona podczas refaktoryzacji zmiany nazwy, w projekcie C#:

![Podgląd zmian](media/previewchanges.png)

W górnej połowie okna zawiera określone wiersze, które zostaną zmienione, każde z nich jest pole wyboru. Możesz sprawdzić lub usuń zaznaczenie pola wyboru każdego pola wyboru, aby umożliwiają selektywne stosowanie refaktoryzacji tylko wybranych wierszy.

Dolnej połowie okna zawiera sformatowany kod z projektu, który zostanie zmieniona z wyróżnioną pozycją obszarów. Wybranie określonego wiersza na górze okna wyróżnione odpowiedniego wiersza w dolnej połowie. Dzięki temu można szybko przejść do odpowiedniej linii i zobacz otaczającego kodu.

Po przejrzeniu zmian, kliknij przycisk **Zastosuj** przycisk, aby zatwierdzić te zmiany lub kliknij przycisk **anulować** przycisk, aby pozostawić rzeczy, jakie były.

## <a name="see-also"></a>Zobacz także

[Refaktoryzacja w programie Visual Studio](../ide/refactoring-in-visual-studio.md)  
[Szybkie akcje](../ide/quick-actions.md)
