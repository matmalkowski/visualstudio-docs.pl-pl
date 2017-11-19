---
title: "Idiastackwalker — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaStackWalker interface
ms.assetid: 4a61a22a-9cf8-4ea1-9e6e-b42f96872d40
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e651c8ba8bee152121b96b14613144768a56cc2f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idiastackwalker"></a>IDiaStackWalker
Zapewnia metody do stosu objaśniono, korzystając z informacji w pliku PDB.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDiaStackWalker: IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDiaStackWalker`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)|Pobiera moduł wyliczający ramki stosu dla x86 platform.|  
|[IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)|Pobiera moduł wyliczający ramki stosu dla typu określonej platformy.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs jest używany do uzyskiwania listy ramek stosu załadować modułu. Każdej z metod jest przekazywany [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) obiektu (zaimplementowana przez aplikację klienta), który zawiera informacje potrzebne do utworzenia listy ramek stosu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Ten interfejs są uzyskiwane przez wywołanie metody `CoCreateInstance` metody za pomocą identyfikatora klasy `CLSID_DiaStackWalker` i identyfikator interfejsu `IID_IDiaStackWalker`. W przykładzie przedstawiono sposób uzyskiwania tego interfejsu.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano, jak uzyskać `IDiaStackWalker` interfejsu.  
  
```C++  
  
      IDiaStackWalker* pStackWalker;  
HRESULT hr = CoCreateInstance(CLSID_DiaStackWalker,  
                              NULL,  
                              CLSCTX_INPROC_SERVER,  
                              IID_IDiaStackWalker,  
                              (void**) &pStackWalker);  
if (FAILED(hr))  
{  
    // Report error and exit  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Dia2.h  
  
 Biblioteki: diaguids.lib  
  
 Biblioteki DLL: msdia80.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy (zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)