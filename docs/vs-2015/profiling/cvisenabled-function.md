---
title: Funkcja CvIsEnabled | Dokumentacja firmy Microsoft
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
- cvmarkers/CvIsEnabledEx
- cvmarkers/CvIsEnabled
helpviewer_keywords:
- CvIsEnabled method
- CvIsEnabledEx method
ms.assetid: 2e4fea6d-758d-4150-8744-6102a1d58c1c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0919e8792743c7d1d953faad88ae6e8385b03993
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42677060"
---
# <a name="cvisenabled-function"></a>CvIsEnabled — Funkcja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [funkcja CvIsEnabled](https://docs.microsoft.com/visualstudio/profiling/cvisenabled-function).  
  
Określa, czy dowolnej sesji ma włączone określonego dostawcy funkcji ETW.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CvIsEnabled(  
   _In_ PCV_PROVIDER pProvider  
);  
HRESULT CvIsEnabledEx(  
   _In_ PCV_PROVIDER pProvider,  
   _In_ CV_IMPORTANCE level,  
   _In_ int category  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `category`  
 Kategoria.  
  
 `level`  
 Poziom ważności.  
  
 `pProvider`  
 Obiekt dostawcy prawidłowe. Nie może mieć wartości NULL.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli dostawca jest obecnie włączona. S_FALSE, jeśli dostawca jest obecnie wyłączona. Kod błędu w przypadku, gdy było żadnych błędów. Aby Sprawdź, czy warunek błędu, a następnie wyszukaj S_OK/S_FALSE, należy użyć makra nie powiodło się.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** cvmarkers.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do biblioteki języka C++](../profiling/cpp-library-reference.md)



