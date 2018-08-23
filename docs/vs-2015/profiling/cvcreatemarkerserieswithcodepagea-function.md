---
title: Funkcja CvCreateMarkerSeriesWithCodePageA | Dokumentacja firmy Microsoft
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
- cvmakers/CvCreateMarkerSeriesWithCodePageA
helpviewer_keywords:
- CvCreateMarkerSeriesWithCodePageA method
ms.assetid: 3d7ed601-2222-4be9-a557-f217db008753
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3716cb41da056590a7978e49f4672d25b1bbdaae
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42682927"
---
# <a name="cvcreatemarkerserieswithcodepagea-function"></a>CvCreateMarkerSeriesWithCodePageA — Funkcja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [funkcja CvCreateMarkerSeriesWithCodePageA](https://docs.microsoft.com/visualstudio/profiling/cvcreatemarkerserieswithcodepagea-function).  
  
Tworzy serię znacznika dla danego dostawcy i określona strona kodowa. Ta funkcja może służyć do określenia strony kodowej jawnie dla tekstu, napisanych przez funkcje API ANSI znacznika. Ustawianie strony kodowej może być przydatne w przypadku, gdy śledzenie jest przechwycony i następnie analizowane na różnych maszynach, za pomocą różnych ustawień regionalnych/języków. Domyślnie używany jest zwrócona przez funkcję GetACP() strony kodowej.  
  
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
 Poprzednio inicjowany przez cvinitprovider — obiekt dostawcy. Nie może mieć wartości NULL.  
  
 `pSeriesName`  
 Nazwa serii znacznika. Nie może mieć wartości NULL, ale dozwolone jest pustym ciągiem.  
  
 `nTextCodePage`  
 Prawidłowy kod strony.  
  
 `ppMarkerSeries`  
 Adres zmiennej danych wyjściowych, który będzie przechowywał znaczników serii kontekstu. Nie może mieć wartości NULL.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK znaczników serii został pomyślnie utworzony lub kod błędu w przypadku zostały wszystkie błędy. Aby sprawdzić, czy warunek błędu, należy użyć makra Powodzenie/niepowodzenie.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** cvmarkers.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do biblioteki języka C++](../profiling/cpp-library-reference.md)



