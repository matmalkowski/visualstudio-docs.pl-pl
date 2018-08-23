---
title: Funkcja CvEnterSpan | Dokumentacja firmy Microsoft
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
- cvmarkers/CvEnterSpanVA
- cvmarkers/CvEnterSpanW
- cvmarkers/CvEnterSpanExW
- cvmarkers/CvEnterSpanA
- cvmarkers/CvEnterSpanExVW
- cvmarkers/CvEnterSpanExA
- cvmarkers/CvEnterSpanVW
helpviewer_keywords:
- CvEnterSpanVW method
- CvEnterSpanVA method
- CvEnterSpanExA method
- CvEnterSpanW method
- CvEnterSpanA method
- CvEnterSpanExVW method
- CvEnterSpanExW method
ms.assetid: 91689e9c-6733-44b9-b36a-8b9b2eef7d1d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 99a3f4d418706ddf282f698ebc25a7cc0e0766a3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42681051"
---
# <a name="cventerspan-function"></a>CvEnterSpan — Funkcja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [funkcja CvEnterSpan](https://docs.microsoft.com/visualstudio/profiling/cventerspan-function).  
  
Oznacza początek nowy zakres.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CvEnterSpanW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,   
    _Out_ PCV_SPAN* ppSpan,   
    _In_ PCWSTR pMessage,  
    ...   
    );   
  
HRESULT CvEnterSpanA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,   
    _Out_ PCV_SPAN* ppSpan,   
    _In_ PCSTR pMessage,   
    ...   
    );   
  
HRESULT CvEnterSpanVW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,   
    _Out_ PCV_SPAN* ppSpan,   
    _In_ PCWSTR pMessage,  
    _In_ va_list argList  
    );   
  
HRESULT CvEnterSpanVA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,   
    _Out_ PCV_SPAN* ppSpan,   
    _In_ PCSTR pMessage,   
    _In_ va_list argList  
    );   
  
HRESULT CvEnterSpanExW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,   
    _In_ CV_IMPORTANCE level,   
    _In_ int category,   
    _Out_ PCV_SPAN* ppSpan,   
    _In_ PCWSTR pMessage,   
    ...   
    );   
  
HRESULT CvEnterSpanExA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,   
    _In_ CV_IMPORTANCE level,   
    _In_ int category,   
    _Out_ PCV_SPAN* ppSpan,   
    _In_ PCSTR pMessage,   
    ...   
    );   
  
HRESULT CvEnterSpanExVW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,   
    _In_ CV_IMPORTANCE level,   
    _In_ int category,   
    _Out_ PCV_SPAN* ppSpan,   
    _In_ PCWSTR pMessage,   
    _In_ va_list argList);   
  
HRESULT CvEnterSpanExVA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,   
    _In_ CV_IMPORTANCE level,   
    _In_ int category,   
    _Out_ PCV_SPAN* ppSpan,   
    _In_ PCSTR pMessage,   
    _In_ va_list argList);  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `argList`  
 Lista argumentów.  
  
 `category`  
 Kategoria zakresu  
  
 `level`  
 Poziom ważności zakresu.  
  
 `pMarkerSeries`  
 Kontekst serii prawidłowe znacznika. Nie może mieć wartości NULL.  
  
 `pMessage`  
 Ciąg formatu komunikatów. Nie może mieć wartości NULL.  
  
 `ppSpan`  
 Adres zmiennej, która będzie zawierać wynikowy obiekt zakresu. Adres nie może mieć wartości NULL, zmienna może mieć dowolną wartość.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, gdy komunikat jest pomyślnie zapisane. Kod błędu w przypadku, gdy było żadnych błędów. Aby sprawdzić, czy warunek błędu, należy użyć makra Powodzenie/niepowodzenie.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** cvmarkers.h  
  
 **Unicode:** cventerspanw —, cventerspanvw —, cventerspanexw — cventerspanexvw —  
  
 **ANSI:** cventerspana —, cventerspanva —, cventerspanexa — cventerspanexvw —  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do biblioteki języka C++](../profiling/cpp-library-reference.md)



