---
title: "Cvcreatedefaultmarkerseriesofdefaultprovider — funkcja | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: cvmarkers/CvCreateDefaultMarkerSeriesOfDefaultProvider
helpviewer_keywords: CvCreateDefaultMarkerSeriesOfDefaultProvider method
ms.assetid: 24eb80f8-8fca-4c47-93b5-bb1eb8ffdffd
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 076a815be9a900b45fffee95856caa003d8155d2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="cvcreatedefaultmarkerseriesofdefaultprovider-function"></a>CvCreateDefaultMarkerSeriesOfDefaultProvider — Funkcja
Tworzy domyślny znacznik serii domyślnego dostawcy.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CvCreateDefaultMarkerSeriesOfDefaultProvider(  
   _Out_ PCV_PROVIDER* ppProvider,  
   _Out_ PCV_MARKERSERIES* ppMarkerSeries  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppProvider`  
 Adres zmiennej obiektu dostawcy. Adres nie może mieć wartości NULL, zmienna może mieć dowolną wartość.  
  
 `ppMarkerSeries`  
 Adres zmiennej obiektu serii znacznika. Adres nie może mieć wartości NULL, zmienna może mieć dowolną wartość.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK podczas serii zarówno dostawcy, jak i znacznika pomyślnie zostały utworzone lub kod błędu w przypadku zostały wszystkie błędy. Użyj makra powiodło się/nie powiodło się, aby sprawdzić warunku błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** cvmarkers.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do biblioteki C++](../profiling/cpp-library-reference.md)