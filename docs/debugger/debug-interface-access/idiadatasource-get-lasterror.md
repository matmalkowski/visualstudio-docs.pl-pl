---
title: IDiaDataSource::get_lastError | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaDataSource::get_lastError method
ms.assetid: cf08850b-8b75-4e8c-90bd-bd0214756f99
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 1a8320a78c807f08d24f6bcc41db9d775850101b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idiadatasourcegetlasterror"></a>IDiaDataSource::get_lastError
Pobiera nazwę pliku dla ostatniego błędu obciążenia.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_lastError (  
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pRetVal  
 [out] Zwraca ciąg zawierający nazwę pliku .pdb skojarzone z ostatniego błędu obciążenia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca kod ostatniego błędu spowodowane operacji ładowania. Zwraca `E_INVALIDARG` Jeśli `pRetVal` parametr jest `NULL`.  
  
## <a name="example"></a>Przykład  
  
```C++  
BSTR    fileName;  
HRESULT errorCode = pSource->get_lastError( &fileName );  
```  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)