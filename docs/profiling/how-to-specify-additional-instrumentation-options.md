---
title: "Porady: Określanie dodatkowych opcji Instrumentacji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.property.advanced
helpviewer_keywords:
- instrumentation, options
- profiling tools, session options
- performance sessions, options
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 8052c0538619588f60fd21802209d57bd7fdf80d
ms.sourcegitcommit: 36ab8429333b31f03992a9fe8fc669db8e09c968
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2018
---
# <a name="how-to-specify-additional-instrumentation-options"></a>Porady: określanie dodatkowych opcji instrumentacji

Można Instrumentacja plików binarnych z za pomocą środowiska IDE programu Visual Studio lub za pomocą narzędzia wiersza polecenia. Instrumentacja pliku binarnego z w środowisku IDE, można kontrolować objętość danych zbieranych podczas instrumentacji, przez określenie dodatkowych opcji Instrumentacji do [VSInstr](../profiling/vsinstr.md) narzędzia. Te opcje są dostępne w sesji lub na poziomie docelowej. Na przykład aby dołączyć lub wykluczyć określone funkcje podczas instrumentacji, opcja dodatkowe Instrumentacji na poziomie docelowej.

> [!IMPORTANT]
> Każdy sondowania włożonego nieco modyfikuje zachowanie oryginalnego programu. Modyfikacja ta powoduje, że obciążenie w czasie analizy. Mimo że zbliżenia ten narzut jest odejmowany, nadal ma skutki niewielkie chronometrażu dla aplikacji wielowątkowych. [VSInstr](../profiling/vsinstr.md) narzędzia do zbierania danych opcje pomocy formantu podczas profilowania.

## <a name="to-specify-additional-instrumentation-option"></a>Aby określić opcję dodatkowe Instrumentacji

1. W **Eksplorator wydajności**, wybierz pozycję **sesji wydajności** , a następnie kliknij prawym przyciskiem myszy i wybierz **właściwości**.

2. W **stron właściwości**, kliknij przycisk **zaawansowane** właściwości.

3. Typ opcji w **dodatkowych opcji Instrumentacji** pole.

     Na przykład użyj /CONTROL:THREAD, aby określić poziom profilowania. Aby uzyskać pełną listę opcji, zobacz [VSInstr](../profiling/vsinstr.md).

4. Kliknij przycisk **OK**.

## <a name="see-also"></a>Zobacz także

[Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)  
[Profilowanie z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md)