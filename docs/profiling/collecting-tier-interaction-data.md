---
title: Zbieranie danych o interakcji między warstwy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.tierinteraction
helpviewer_keywords:
- Profiling Tools,ADO.NET profiling
- tier interaction profiling method
- Profiling Tools,tier-interaction method
- ADO.NET performance profiling
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f5e86cd1318d4b0db35ce6fa0e0abd925100fe34
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34548440"
---
# <a name="collect-tier-interaction-data"></a>Zbieranie danych o interakcji między warstwami

Profilowanie interakcji między warstwami udostępnia dodatkowe informacje o czas wykonywania funkcji aplikacji wielowarstwowych, które komunikują się z bazami danych za pośrednictwem usług ADO.NET. Dane są zbierane tylko dla wywołań synchronicznych funkcji.

**Wersje Visual Studio**

Interakcja warstwowa profilowania danych mogą być zbierane przy użyciu dowolnej wersji programu Visual Studio. Jednak dane profilowania interakcji warstwy można wyświetlić tylko w programie Visual Studio Enterprise.

**Windows 8 i Windows Server 2012**

Aby zbierać dane interakcji warstwy aplikacji klasycznych systemu Windows 8 i aplikacji systemu Windows Server 2012, należy użyć metody instrumentacji. Nie można zebrać danych o interakcji między warstwy dla aplikacji platformy uniwersalnej systemu Windows. Zobacz [narzędzi wydajności w przypadku aplikacji systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md). Warstwa danych o interakcji między mogą obejmować wszystkie metody profilowania w innej wersji systemu Windows.

**Kreator wydajności**

Z powodu błędu w Kreatorze wydajności należy dodać opcję zbierania danych interakcji warstwy do uruchomienia profilowania w Eksploratorze wydajności. Należy również dodać projekt, plik wykonywalny lub witryny sieci Web do węzła docelowego Eksplorator wydajności.

## <a name="to-add-tier-interaction-data-to-a-profiling-run-by-using-the-performance-session-property-pages"></a>Aby dodać warstwę danych o interakcji między do profilowania uruchamiania za pomocą stron właściwości sesji wydajności

1. W Eksploratorze wydajności wybierz **właściwości** z menu kontekstowego.

2. Wybierz **interakcje warstw** strony, a następnie sprawdź **Włącz profilowanie interakcji między warstwami** pole wyboru.

3. W Eksploratorze wydajności wybierz **cele** węzeł, a następnie określ projekt, plik wykonywalny lub witryny sieci web, który ma zostać profilu.

## <a name="see-also"></a>Zobacz także

[Widok interakcji warstwowych](../profiling/tier-interactions-view.md)