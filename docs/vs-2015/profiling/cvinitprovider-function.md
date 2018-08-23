---
title: Funkcja CvInitProvider | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- cvmarkers/CvInitProvider
helpviewer_keywords:
- CvInitProvider method
ms.assetid: ba1863ad-e35f-4d34-a2f2-5e68957d1915
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a65df9e9ccc61aec0a96f5f467962d46eb88b78c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42680655"
---
# <a name="cvinitprovider-function"></a>CvInitProvider — Funkcja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [funkcja CvInitProvider](https://docs.microsoft.com/visualstudio/profiling/cvinitprovider-function).  
  
Inicjuje dostawcę znaczników narzędzia. Musi zostać wywołana przed wszystkie inne funkcje SDK narzędzia Concurrency Visualizer.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CvInitProvider(  
   _In_ const GUID* pGuid,  
   _Out_ PCV_PROVIDER* ppProvider  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pGuid`  
 Identyfikator guid dostawcy. Nie może mieć wartości NULL.  
  
 `ppProvider`  
 Adres zmiennej danych wyjściowych, który będzie przechowywał kontekstu dostawcy. Nie może mieć wartości NULL.  
  
## <a name="return-value"></a>Wartość zwracana  
 Pomyślnie zainicjowano dostawcy lub kod błędu w przypadku zostały wszystkie błędy, S_OK. Aby sprawdzić, czy warunek błędu, należy użyć makra Powodzenie/niepowodzenie.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** cvmarkers.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do biblioteki języka C++](../profiling/cpp-library-reference.md)



