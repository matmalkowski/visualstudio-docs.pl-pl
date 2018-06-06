---
title: 'DA0501: Średnie wykorzystanie CPU przez proces poddawany profilowaniu. | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DA0501
- vs.performance.DA0501
- vs.performance.501
ms.assetid: b01946b4-75e3-47d5-a1a1-cebfae66a3af
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 97e011225f84f1c5f3adcfc050260e870232fa33
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2018
ms.locfileid: "34766103"
---
# <a name="da0501-average-cpu-consumption-by-the-process-being-profiled"></a>DA0501: Średnie wykorzystanie CPU przez proces poddawany profilowaniu.
|||  
|-|-|  
|Identyfikator reguły|DA501|  
|Kategoria|Monitorowanie zasobów|  
|Metoda profilowania|Wszystkie|  
|Komunikat|Średnie użycie Procesora przez profilowany proces.|  
|Typ reguły|Informacje|  
  
 Gdy profilu można za pomocą próbkowania, pamięci platformy .NET lub metody kontencji zasobów, należy zebrać co najmniej 10 próbek do wyzwolenia tej reguły.  
  
## <a name="rule-description"></a>Opis reguły  
 Ten komunikat raporty procent czasu, który procesor był zajęty wykonywaniem instrukcji z aplikacji. Podanej wartości jest średnią we wszystkich interwałach pomiarowych, w których był aktywny PROFILOWANEGO procesu. Wartość może być większa niż 100% na maszynie z więcej niż jeden procesor.  
  
## <a name="how-to-use-rule-data"></a>Jak używać danych reguły  
 Porównanie wydajności z różnych wersji lub kompilacji programu lub zrozumieć wydajność aplikacji w scenariuszach różnych testu, należy użyć wartości reguły.