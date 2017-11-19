---
title: "marker_series — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: cvmarkersobj/Concurrency::diagnostic::marker_series
helpviewer_keywords: Concurrency::diagnostic::marker_series class
ms.assetid: b8445ed0-c512-4f92-b6b4-3d05c044f939
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b326e88e18e3a7c5515cc11bfda7e5c35ae4a063
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="markerseries-class"></a>marker_series — Klasa
Reprezentuje serial kanału zdarzeń generowanych przez jednego dostawcę.  
  
## <a name="syntax"></a>Składnia  
  
```  
class marker_series;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[marker_series::marker_series — Konstruktor](../profiling/marker-series-marker-series-constructor.md)|Inicjuje nowe wystąpienie klasy `marker_series` klasy.|  
|[marker_series:: ~ marker_series — destruktor](../profiling/marker-series-tilde-marker-series-destructor.md)|Niszczy obiektu marker_series i zwalnia wszystkie zasoby przydzielone.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[marker_series::is_enabled — metoda](../profiling/marker-series-is-enabled-method.md)|Określa, czy dowolnej sesji jest włączony dostawca.|  
|[marker_series::write_alert — metoda](../profiling/marker-series-write-alert-method.md)|Zapisuje plik śledzenia Concurrency Visualizer alertu.|  
|[marker_series::write_flag — metoda](../profiling/marker-series-write-flag-method.md)|Zapisuje plik śledzenia Concurrency Visualizer flagę.|  
|[marker_series::write_message — metoda](../profiling/marker-series-write-message-method.md)|Zapisuje komunikat do pliku śledzenia wizualizatora współbieżności.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `marker_series`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** cvmarkersobj.h  
  
 **Namespace:** CONCURRENCY::Diagnostic —  
  
## <a name="see-also"></a>Zobacz też  
 [Namespace diagnostycznych](../profiling/diagnostic-namespace.md)