---
title: Funkcja SccUninitialize | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccUninitialize
helpviewer_keywords: SccUninitialize function
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5976313939ee9efa81c71e7894da8e5f45e2d017
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="sccuninitialize-function"></a>Funkcja SccUninitialize
Ta funkcja czyści wszystkie alokacji lub otwarte połączenia utworzony przez poprzednie wywołanie [SccInitialize](../extensibility/sccinitialize-function.md) w ramach przygotowania do zamykania wtyczkę kontroli źródła.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
SCCRTN SccUninitialize (  
   LPVOID pvContext  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pvContext  
 [in] Wskaźnik do struktury kontekstu wtyczkę kontroli źródła utworzone w [SccInitialize](../extensibility/sccinitialize-function.md).  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczkę kontroli źródła tej funkcji może przywrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Oczyszczania została ukończona pomyślnie.|  
  
## <a name="remarks"></a>Uwagi  
 Wtyczkę kontroli źródła jest odpowiedzialny za przygotowywanie wyłączyć i zwalnianie pamięci przydzielonej wtyczki dla struktury kontekstu. Funkcja jest wywoływana raz dla każdego wystąpienia danego dodatku typu plug-in. Wywołanie [SccInitialize](../extensibility/sccinitialize-function.md) poprzedza tego wywołania. Brak projektów nadal może być otwarty w momencie wywołania `SccUninitialize`.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje API wtyczkę kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)