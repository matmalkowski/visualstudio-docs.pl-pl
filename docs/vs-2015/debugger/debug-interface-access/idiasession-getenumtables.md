---
title: Idiasession::getenumtables — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::getEnumTables method
ms.assetid: 66e0fba2-ca63-4e24-a46a-c99c7fb61dd1
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c8937bd1a04d8856c2b2a7b18c5a05e91a8070d7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42695568"
---
# <a name="idiasessiongetenumtables"></a>IDiaSession::getEnumTables
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [idiasession::getenumtables —](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasession-getenumtables).  
  
Pobiera moduł wyliczający dla wszystkich tabel znajdujących się w magazynie symboli.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT getEnumTables (   
   IDiaEnumTables** ppEnumTables  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppEnumTables`  
 [out] Zwraca [idiaenumtables —](../../debugger/debug-interface-access/idiaenumtables.md) obiektu. Używaj tego interfejsu, można wyliczyć tabel w magazynie symboli.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono ogólne funkcję, która używa `getEnumTables` metodę, aby uzyskać obiekt określonego modułu wyliczającego. Jeśli moduł wyliczający zostanie znaleziony, funkcja zwraca wskaźnik, który może być rzutowany na żądanego interfejsu; w przeciwnym razie funkcja zwraca `NULL`.  
  
```cpp#  
IUnknown *GetTable(IDiaSession *pSession, REFIID iid)  
{  
    IUnknown *pUnknown = NULL;  
    if (pSession != NULL)  
    {  
        CComPtr<IDiaEnumTables> pEnumTables;  
        if (pSession->getEnumTables(&pEnumTables) == S_OK)  
        {  
             CComPtr<IDiaTable> pTable;  
             DWORD celt = 0;  
             while(pEnumTables->Next(1,&pTable,&celt) == S_OK &&  
                   celt == 1)  
             {  
                  if (pTable->QueryInterface(iid, (void **)pUnknown) == S_OK)  
                  {  
                       break;  
                  }  
                  pTable = NULL;  
             }  
        }  
    }  
    return(pUnknown);  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Idiaenumtables —](../../debugger/debug-interface-access/idiaenumtables.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)



