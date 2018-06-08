---
title: 'Porady: Określanie plików binarnych do uruchomienia | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.itemlaunch
helpviewer_keywords:
- profiling tools, launching
- performance tools, launching
- performance sessions, launching
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 87fc4102b3cbd3420f1e5c3b7ea4a067e0d95a0d
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2018
ms.locfileid: "34844862"
---
# <a name="how-to-specify-the-binary-to-start"></a>Porady: Określanie plików binarnych do uruchomienia

Aby profil plików binarnych takich jak biblioteki dll, należy wprowadzić informacje w  **\<docelowy > strony właściwości** okno dialogowe. Te informacje wskazuje, gdzie znaleźć aplikacja wywołująca projektu biblioteki DLL.

1. W **Eksplorator wydajności**, kliknij prawym przyciskiem myszy docelowy plik binarny, a następnie kliknij przycisk **właściwości**.

2. W **strony właściwości** okno dialogowe, kliknij przycisk **uruchamianie** właściwości.

3. Wybierz **zastąpienie właściwości projektu** pole wyboru.

4. W **pliku wykonywalnego do uruchomienia** tekst Określ lokalizację pliku.

5. W **argumenty** tekst określ argumenty, które są wymagane do uruchomienia aplikacji.

6. W **katalog roboczy** tekst Określ lokalizację katalogu.

7. Kliknij przycisk **OK**.

## <a name="see-also"></a>Zobacz także

[Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)