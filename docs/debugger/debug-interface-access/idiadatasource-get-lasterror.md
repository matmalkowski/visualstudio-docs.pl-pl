---
title: IDiaDataSource::get_lastError | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::get_lastError method
ms.assetid: cf08850b-8b75-4e8c-90bd-bd0214756f99
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 08d17e0532d4d5d987d69afa7de062a193371950
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
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