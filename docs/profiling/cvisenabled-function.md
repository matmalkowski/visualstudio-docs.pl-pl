---
title: "Cvisenabled — funkcja | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- cvmarkers/CvIsEnabledEx
- cvmarkers/CvIsEnabled
helpviewer_keywords:
- CvIsEnabled method
- CvIsEnabledEx method
ms.assetid: 2e4fea6d-758d-4150-8744-6102a1d58c1c
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 50dc5727ab98f09ada660c2d92c07d908f71c548
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="cvisenabled-function"></a>CvIsEnabled — Funkcja
Określa, czy dowolnej sesji jest włączony określonego dostawcy ETW.  
  
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
 Obiekt prawidłowego dostawcy. Nie może mieć wartości NULL.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość S_OK, gdy dostawca jest aktualnie włączony. Wartości S_FALSE, jeśli dostawca jest wyłączony. Kod błędu w przypadku, gdy było żadnych błędów. Użyć makra nie można sprawdzić warunku błędu, a następnie wyszukaj S_OK/S_FALSE.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** cvmarkers.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do biblioteki C++](../profiling/cpp-library-reference.md)