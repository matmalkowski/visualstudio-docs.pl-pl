---
title: IDebugAddress | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugAddress
helpviewer_keywords:
- IDebugAddress interface
ms.assetid: bc709ff7-4966-4f36-9af2-690efe2cea1d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ace2892d4518de8c5a4abaa2c113df914f9fa6b1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31100247"
---
# <a name="idebugaddress"></a>IDebugAddress
Ten interfejs reprezentuje adres elementu. Jest zwracany przez program obsługi symboli.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugAddress : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Dostawca symbol implementuje ten interfejs reprezentuje adres obiektu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wiele metod w wielu interfejsach zwrócić tego interfejsu.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 Ten interfejs implementuje następującą metodę:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)|Pobiera [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) struktury opisujące obiekt i jego lokalizacji.|  
  
## <a name="remarks"></a>Uwagi  
 Dostawca symbol zwraca ten interfejs reprezentujący obiekt i jego lokalizacji w ramach określonego zakresu (na przykład funkcji, metody lub klasy). Ten interfejs jest zwracana z i przekazane do różnych metod symbol dostawcy i wyrażenie ewaluatora. Zazwyczaj dostawcy symbol jest tylko jednostki, które należy interpretować zawartość tego interfejsu.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Symbol dostawcy interfejsów](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)