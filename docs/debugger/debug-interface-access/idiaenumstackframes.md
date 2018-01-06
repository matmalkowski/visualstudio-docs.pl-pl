---
title: "Idiaenumstackframes — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumStackFrames interface
ms.assetid: 3d1e8403-c9fc-42ff-ae35-0ab9a5ed2ad7
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f9c4c81fcecb76cc094297cb8fa5c733a677a831
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idiaenumstackframes"></a>IDiaEnumStackFrames
Wylicza różnych dostępnych ramek stosu.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDiaEnumStackFrames::Next](../../debugger/debug-interface-access/idiaenumstackframes-next.md)|Pobiera określoną liczbę elementów w ramce stosu z sekwencji wyliczenia.|  
|[IDiaEnumStackFrames::Reset](../../debugger/debug-interface-access/idiaenumstackframes-reset.md)|Resetuje sekwencję wyliczenia na początku.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Uzyskanie przez wywołanie metody tego interfejsu [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) lub [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md) metody.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono sposób uzyskiwania i używania `IDiaEnumStackFrames` interfejsu. Zobacz [idiastackframe —](../../debugger/debug-interface-access/idiastackframe.md) interfejs dla implementacji `PrintStackFrame` funkcji.  
  
```C++  
void DumpStackFrames(IDiaStackWalker*     pStackWalker,  
                     IDiaStackWalkHelper* pStackWalkHelper,  
                     CV_CPU_TYPE_e        cpuType)  
{  
    if (pStackWalker != NULL && pStackWalkHelper != NULL)  
    {  
        CComPtr<IDiaEnumStackFrames> pEnumsFrames;  
        HRESULT hr;  
        hr = pStackWalker->getEnumFrames2(cpuType, pStackWalkHelper, &pEnumFrames);  
        if (SUCCEEDED(hr) && pEnumFrames != NULL)  
        {  
             CComPtr<IDiaStackFrame> pStackFrame;  
             DWORD celt = 0;  
  
             while (pEnumFrames->Next(1, &pStackFrame, &celt) == S_OK)  
             {  
                 PrintStackFrame(pStackFrame);  
             }  
             pStackFrame = NULL;  
        }  
    }  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Dia2.h  
  
 Biblioteki: diaguids.lib  
  
 Biblioteki DLL: msdia80.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy (zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Idiastackwalkframe —](../../debugger/debug-interface-access/idiastackwalkframe.md)   
 [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)   
 [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)