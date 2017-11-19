---
title: Zachowanie edytora | Dokumentacja firmy Microsoft
description: 
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 81EE4460-26EB-4BB0-9297-932E1F88E4B8
ms.openlocfilehash: 3515dfbf3a7cf8c23178aa9df243638f955593e9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="editor-behavior"></a>Zachowanie edytora

Edytor zachowania można ustawić kodu do sformatowania w niezmienionej postaci. Te akcje są ustawione w obszarze **programu Visual Studio > Preferencje... > Edytor tekstu > zachowanie**, niektóre z najczęściej używane funkcje są opisane poniżej:

![Opcje edytora zachowania](media/source-editor-image9.png)

*  Dopasowywanie klamrowe nawiasy zamykające mogą być dodawane automatycznie do kodu podczas tworzenia nowej klasy, metody lub właściwości. Gdy ta opcja jest zaznaczona, wpisując `{` automatycznie doda `}`.
* Formatowanie kodu na bieżąco jest wyzwalany przez naciśnięcie znaków, takich jak średnikami lub nawiasy klamrowe, które będą emulować preferencje formatowania, które są ustawione.
* Można również format pliku, zapisując go, co umożliwia pisanie kodu zgodnie z potrzebami i pozostawienie odpowiedzialny za formatowanie kodu zgodnie z ustaleniami według preferencji istniejącego środowiska IDE.
* Wcięcie można wartość None, Auto, lub inteligentne. Te należy wykonać następujące czynności:
 * Brak - ustawia karetkę na początek następnego wiersza
 * Auto - ustawia karetkę do tej samej kolumny w następnym wierszu
 * Inteligentne - wcięć na następujący wiersz na podstawie kodu
* Dzielenie wyrazów zachowanie różni się od systemów operacyjnych i do celów nawigacji, Edytor tekstu musi wiedzieć, gdzie słowa rozpoczynać się ani kończyć. Formatowanie można ustawić Unix lub systemu Windows.

Można również ustawić reguły formatowania XML, CSS, HTML i JSON.