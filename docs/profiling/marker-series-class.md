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
ms.workload: multiple
ms.openlocfilehash: 9bb2cbe0a87e61a50f3f2b071aef9ef9e12663a0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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
|[Konstruktor marker_series::marker_series](../profiling/marker-series-marker-series-constructor.md)|Inicjuje nowe wystąpienie klasy `marker_series` klasy.|  
|[Destruktor marker_series::~marker_series](../profiling/marker-series-tilde-marker-series-destructor.md)|Niszczy obiektu marker_series i zwalnia wszystkie zasoby przydzielone.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Metoda marker_series::is_enabled](../profiling/marker-series-is-enabled-method.md)|Określa, czy dowolnej sesji jest włączony dostawca.|  
|[Metoda marker_series::write_alert](../profiling/marker-series-write-alert-method.md)|Zapisuje plik śledzenia Concurrency Visualizer alertu.|  
|[Metoda marker_series::write_flag](../profiling/marker-series-write-flag-method.md)|Zapisuje plik śledzenia Concurrency Visualizer flagę.|  
|[Metoda marker_series::write_message](../profiling/marker-series-write-message-method.md)|Zapisuje komunikat do pliku śledzenia wizualizatora współbieżności.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `marker_series`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** cvmarkersobj.h  
  
 **Namespace:** CONCURRENCY::Diagnostic —  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw diagnostic](../profiling/diagnostic-namespace.md)