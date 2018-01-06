---
title: IEEDataStorage | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEEDataStorage
helpviewer_keywords: IEEDataStorage interface
ms.assetid: 704e932d-2325-410e-89c4-ce88c6ec19da
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7a28b738c757924f2a3c588d52ea896dc6301384
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ieedatastorage"></a>IEEDataStorage
Ten interfejs reprezentuje tablicę bajtów.  
  
## <a name="syntax"></a>Składnia  
  
```  
IEEDataStorage : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Ewaluator wyrażeń (EE) implementuje ten interfejs do reprezentowania tablicę bajtów (używany przez wizualizatorach typu do pobierania i zmian w danych za pośrednictwem [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) interfejs). EE zwykle implementuje ten interfejs obsługuje wizualizatorach typu zewnętrznego.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Metody w `IPropertyProxyEESide` interfejsu wszystkich zwrócić tego interfejsu. Wywołanie [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) uzyskanie [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) interfejsu. Wywołanie [QueryInterface](/cpp/atl/queryinterface) na [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interfejsu uzyskanie [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) interfejsu.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 `IEEDataStorage` Implementuje interfejs następujące metody:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)|Pobiera określoną liczbę bajtów danych do dostarczonego buforu.|  
|[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|Pobiera liczba dostępnych bajtów danych.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs jest używany przez wizualizatora typ dostępu do danych przechowywanych przez konkretnego obiektu. Dane są traktowane jako tablicę bajtów, umożliwiając wizualizatora typu do manipulowania go w dowolnie wybrany sposób jest wymagany do wyświetlane dla użytkownika.  
  
 Podglądu niestandardowego może również używać tego interfejsu w razie potrzeby, chociaż więcej zwykle podglądu niestandardowego użyje niestandardowego interfejsu [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) lub [GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md) (dla dane zorientowane na ciąg znaków).  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Core](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [Wizualizator typów i przeglądarka niestandardowa](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)