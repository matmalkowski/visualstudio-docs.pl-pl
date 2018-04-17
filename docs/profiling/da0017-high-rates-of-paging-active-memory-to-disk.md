---
title: 'DA0017: Wysoki stopień stronicowania aktywnej pamięci na dysk | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.17
- vs.performance.rules.DA0017
- vs.performance.DA0017
ms.assetid: 01011eec-5930-43b3-980d-2cb01e2ca7f6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ded3ac27f9b28fd39799366e4e7add009452160a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="da0017-high-rates-of-paging-active-memory-to-disk"></a>DA0017: Wysoki stopień stronicowania aktywnej pamięci na dysku
|||  
|-|-|  
|Identyfikator reguły|DA0017|  
|Kategoria|Pamięci i stronicowania|  
|Metoda profilowania|Wszystkie|  
|Komunikat|Występuje intensywne stronicowanie aktywnej pamięci na dysk. Ta aplikacja może być zależna od pamięci.|  
|Typ reguły|Informacje|  
  
 Gdy profilu można za pomocą próbkowania, pamięci platformy .NET lub metody kontencji zasobów, należy zebrać co najmniej 10 próbek do wyzwolenia tej reguły.  
  
## <a name="cause"></a>Przyczyna  
 Dane o wydajności systemu, który został zebrany w przebiegu profilowania wskazuje intensywne stronicowanie aktywnej pamięci do i z dysku, które wystąpiły w przebiegu profilowania. Stawki stronicowania na tym poziomie zazwyczaj będzie miało wpływ wydajność aplikacji i elastyczność. Rozważ zmniejszenie przez modyfikowanie algorytmów alokacji pamięci. Masz może również wziąć pod uwagę wymagania dotyczące pamięci aplikacji.  
  
## <a name="rule-description"></a>Opis reguły  
  
> [!NOTE]
>  Ta zasada informacyjną generowane, gdy stopień stronicowania aktywnej pamięci osiągnąć znaczną ilość. Gdy występuje wyjątkowo wysoki stopień stronicowania, zasada ostrzeżenia [DA0014: wyjątkowo wysoki stopień stronicowania aktywnej pamięci na dysk](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md) generowane zamiast tego.  
  
 Nadmiernego stronicowania na dysku może być spowodowane brakiem pamięci fizycznej. Jeśli operacja stronicowania dominują w aplikacjach użycie dysku fizycznego, w którym znajduje się plik stronicowania, mogą one spowolnić inne operacje dysku ukierunkowane na zastosowanie do tego samego dysku.  
  
 Strony są często dysku zapisu lub odczytu z dysku podczas operacji stronicowania zbiorczego. Liczba stron wyjścia na sekundę często jest znacznie większa niż liczba zapisy stron/s, na przykład. Ponieważ dane wyjściowe strony na sekundę obejmuje również strony zmienione dane z pamięci podręcznej systemu plików. Jednak nie zawsze jest łatwo określić, które procesy są bezpośrednio odpowiedzialne za stronicowania lub dlaczego.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Kliknij dwukrotnie komunikat w oknie Lista błędów, aby przejść do [znaczniki](../profiling/marks-view.md) widoku. Znajdź **Pamięć\Strony/s** kolumny. Określa, czy określone fazy wykonywania programu stronicowania działania We/Wy w przypadku większych niż inne.  
  
 Jeśli zbiera dane profilu dla aplikacji ASP.NET w scenariuszu testowania obciążenia, spróbuj uruchomić ponownie test obciążenia na komputerze, skonfigurować przy użyciu dodatkowej pamięci fizycznej (lub pamięci RAM).  
  
 Rozważ zmniejszenie przydziału pamięci zmiana algorytmów i unikanie pamięć interfejsów API, takich jak String.concat — i String.Substring.