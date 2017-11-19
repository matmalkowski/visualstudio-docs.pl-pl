---
title: "Cvcreatemarkerserieswithcodepagea — funkcja | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: cvmakers/CvCreateMarkerSeriesWithCodePageA
helpviewer_keywords: CvCreateMarkerSeriesWithCodePageA method
ms.assetid: 3d7ed601-2222-4be9-a557-f217db008753
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cc266ff4a96fa96f89e1eaafe2eaa8377ef601fa
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="cvcreatemarkerserieswithcodepagea-function"></a>CvCreateMarkerSeriesWithCodePageA — Funkcja
Tworzy serię znacznika dla danego dostawcy i określona strona kodowa. Ta funkcja umożliwia określanie strony kodowej jawnie dla tekstu zapisywane przez funkcje interfejsu API ANSI znacznika. Ustawianie strony kodowej mogą być przydatne w przypadku, gdy śledzenie jest przechwycony i następnie przeanalizowane na kilka różnych maszyn z różnych ustawień regionalnych/języków. Domyślnie używany jest zwracane przez funkcję GetACP() stronę kodową.  
  
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
 [Odwołanie do biblioteki C++](../profiling/cpp-library-reference.md)