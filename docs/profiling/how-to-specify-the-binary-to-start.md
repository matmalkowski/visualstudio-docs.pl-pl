---
title: "Porady: Określanie plików binarnych do uruchomienia | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.property.itemlaunch
helpviewer_keywords:
- profiling tools, launching
- performance tools, launching
- performance sessions, launching
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 94dbedfaa008b83ac45cea9afaa6bac2a254e77e
ms.sourcegitcommit: 36ab8429333b31f03992a9fe8fc669db8e09c968
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2018
---
# <a name="how-to-specify-the-binary-to-start"></a>Porady: określanie plików binarnych do uruchomienia

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