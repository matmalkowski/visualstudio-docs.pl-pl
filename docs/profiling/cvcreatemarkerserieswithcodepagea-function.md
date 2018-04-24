---
title: Cvcreatemarkerserieswithcodepagea — funkcja | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmakers/CvCreateMarkerSeriesWithCodePageA
helpviewer_keywords:
- CvCreateMarkerSeriesWithCodePageA method
ms.assetid: 3d7ed601-2222-4be9-a557-f217db008753
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3bf258dbca695fe3f1516d977e02a21058377e02
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="cvcreatemarkerserieswithcodepagea-function"></a>CvCreateMarkerSeriesWithCodePageA — Funkcja
Tworzy serię znacznika dla danego dostawcy oraz określonej strony kodowej. Ta funkcja umożliwia określanie strony kodowej jawnie dla tekstu zapisywane przez funkcje interfejsu API ANSI znacznika. Ustawianie strony kodowej mogą być przydatne w przypadku, gdy śledzenie jest przechwycony i następnie przeanalizowane na kilka różnych maszyn z różnych ustawień regionalnych/języków. Domyślnie używany jest zwracane przez funkcję GetACP() stronę kodową.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CvCreateMarkerSeriesWithCodePageA(  
   _In_ PCV_PROVIDER pProvider,  
   _In_ LPCSTR pSeriesName,  
   _In_ UINT nTextCodePage,  
   _Out_ PCV_MARKERSERIES* ppMarkerSeries  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pProvider`  
 Obiekt dostawcy poprzednio inicjowany przez CvInitProvider. Nie może mieć wartości NULL.  
  
 `pSeriesName`  
 Nazwa serii znacznika. Nie może mieć wartości NULL, ale może być ciągiem pustym.  
  
 `nTextCodePage`  
 Strona prawidłowy kod.  
  
 `ppMarkerSeries`  
 Adres zmiennej danych wyjściowych, która zapisze w kontekście serii znacznika. Nie może mieć wartości NULL.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK serii znacznika został utworzony pomyślnie lub kod błędu w przypadku zostały wszystkie błędy. Użyj makra powiodło się/nie powiodło się, aby sprawdzić warunku błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** cvmarkers.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do biblioteki języka C++](../profiling/cpp-library-reference.md)