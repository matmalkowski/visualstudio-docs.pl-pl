---
title: Cvreleaseprovider — funkcja | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvReleaseProvider
helpviewer_keywords:
- CvReleaseProvider method
ms.assetid: 8d74379e-295d-452b-bd5f-0769df387d4f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f0b54fc676a9e7e6ee523bba7f94f58aef49916b
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="cvreleaseprovider-function"></a>CvReleaseProvider — Funkcja
Dostawca znacznika wersjach. Zwalnianie dostawcy znacznika nie wpłynie na utworzonej wcześniej znacznika serii tego dostawcy. Znacznika serie mają być wersji oddzielnie przez wywołanie CvReleaseMarkerSeries. Błąd zwolnienia dostawcy spowoduje przeciek pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CvReleaseProvider(  
   _In_ PCV_PROVIDER pProvider  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pProvider`  
 Kontekst dostawcy. Nie może mieć wartości NULL.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK pomyślnie zwolnieniu dostawcy lub kod błędu w przypadku zostały wszystkie błędy. Użyj makra powiodło się/nie powiodło się, aby sprawdzić warunku błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** cvmarkers.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do biblioteki języka C++](../profiling/cpp-library-reference.md)