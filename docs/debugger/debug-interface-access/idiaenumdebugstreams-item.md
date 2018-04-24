---
title: IDiaEnumDebugStreams::Item | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreams::Item method
ms.assetid: 6b388fe1-eabc-4720-9d59-dc09b0ceaeac
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b255a96b3bd443ff4a2782cb2161694da3694c17
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="idiaenumdebugstreamsitem"></a>IDiaEnumDebugStreams::Item
Pobiera strumień debugowania za pomocą indeksu lub name.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT Item (   
   VARIANT                   index,  
   IDiaEnumDebugStreamData** stream  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 indeks  
 [in] Indeks lub nazwa strumień debugowania do pobrania. Jeśli variant liczba całkowita jest używany, musi być w zakresie od 0 do `count`-1, gdzie `count` jest zwracane przez [IDiaEnumDebugStreams::get_Count](../../debugger/debug-interface-access/idiaenumdebugstreams-get-count.md) metody.  
  
 strumień  
 [out] Zwraca [idiaenumdebugstreamdata —](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md) obiekt reprezentujący debugowania określonego strumienia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="example"></a>Przykład  
  
```C++  
IDiaEnumDebugStreamData *GetStreamData(IDiaEnumDebugStreams *pStreamList,  
                                       LONG whichStream)  
{  
    IDiaEnumDebugStreamData *pStreamData = NULL;  
    if (pStreamList != NULL)  
    {  
        LONG numStreams = 0;  
        if (pStreamList->get_count(&numStreams) == S_OK &&  
            whichStream >= 0 && whichStream < numStreams)  
        {  
            VARIANT vIndex;  
            vIndex.vt   = VT_I4;  
            vIndex.lVal = whichStream;  
            if (pStreamList->Item(vIndex,&pStreamData) != S_OK)  
            {  
                 std::cerr << "Error retrieving stream " << whichStream << std::endl;  
            }  
        }  
    }  
    return(pStreamData);  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Idiaenumdebugstreamdata —](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)   
 [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)