---
title: IEnumDebugAddresses | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEnumDebugAddresses
helpviewer_keywords:
- IEnumDebugAddresses interface
ms.assetid: 5f6f6751-e6d8-4c5a-8e81-414b6e5d8cc5
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: db0104485d960cfbeedc257c1a47ad627776dc03
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42679278"
---
# <a name="ienumdebugaddresses"></a>IEnumDebugAddresses
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [IEnumDebugAddresses](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ienumdebugaddresses).  
  
Ten interfejs reprezentuje kolekcję obiektów Implementowanie [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IEnumDebugAdresses : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Ten interfejs jest implementowany przez dostawcę symbol zapewnienie zestawów obiektów, które implementują [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfejsu. Pamiętaj, że nie jest standardowy wyliczanie modelu COM z powodu obecności [GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md) metody.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Ten interfejs jest zwracany przez [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md) i [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md).  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 Ten interfejs implementuje są następujące metody.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Next](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)|Pobiera następny zestaw [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) obiektów z wyliczenia.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugaddresses-skip.md)|Pomija określoną liczbę pozycji.|  
|[Resetuj](../../../extensibility/debugger/reference/ienumdebugaddresses-reset.md)|Resetuje wyliczenia do pierwszej pozycji.|  
|[Klon](../../../extensibility/debugger/reference/ienumdebugaddresses-clone.md)|Pobiera kopię bieżącego wyliczenia.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md)|Pobiera liczbę wpisów w wyliczeniu.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs jest zwykle używany przez aparat debugowania w celu określenia odpowiedniego adresu oferowanie Ewaluator wyrażeń.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy dostawca symboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)   
 [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)

