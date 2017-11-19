---
title: "CvInitProvider — funkcja | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: cvmarkers/CvInitProvider
helpviewer_keywords: CvInitProvider method
ms.assetid: ba1863ad-e35f-4d34-a2f2-5e68957d1915
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0ddb249c825048b5bb98dd5b648902663ccd85a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="cvinitprovider-function"></a>CvInitProvider — Funkcja
Inicjuje dostawcę znacznika. Musi zostać wywołana przed jakichkolwiek innych funkcji zestawu SDK wizualizatora współbieżności.  
  
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
 Adres zmiennej wyjściowego, który będzie przechowywał kontekstu dostawcy. Nie może mieć wartości NULL.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość S_OK, gdy dostawca pomyślnie zainicjowano lub kod błędu w przypadku zostały wszystkie błędy. Użyj makra powiodło się/nie powiodło się, aby sprawdzić warunku błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** cvmarkers.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do biblioteki C++](../profiling/cpp-library-reference.md)