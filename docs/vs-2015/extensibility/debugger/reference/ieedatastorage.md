---
title: IEEDataStorage | Dokumentacja firmy Microsoft
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
- IEEDataStorage
helpviewer_keywords:
- IEEDataStorage interface
ms.assetid: 704e932d-2325-410e-89c4-ce88c6ec19da
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b5a59a2284b691bbbc7a7bfe1798fc601d5051fb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42679522"
---
# <a name="ieedatastorage"></a>IEEDataStorage
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [IEEDataStorage](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ieedatastorage).  
  
Ten interfejs reprezentuje tablicę bajtów.  
  
## <a name="syntax"></a>Składnia  
  
```  
IEEDataStorage : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Ewaluator wyrażeń (EE) implementuje ten interfejs reprezentujący tablicę bajtów (używane przez wizualizatorów typu do pobierania danych i ich zmienianie za pośrednictwem [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) interfejsu). EE zwykle implementuje ten interfejs obsługuje wizualizatorów typu zewnętrznego.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Metody na `IPropertyProxyEESide` interfejsu wszystkie zwracać ten interfejs. Wywołaj [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) uzyskać [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) interfejsu. Wywołaj [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) na [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interfejs w celu uzyskania [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) interfejsu.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 `IEEDataStorage` Interfejsu implementuje następujące metody:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)|Pobiera określoną liczbę bajtów danych do dostarczony bufor.|  
|[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|Pobiera liczba dostępnych bajtów danych.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs jest używany przez Wizualizator typów dostępu do danych przechowywanych przez konkretnego obiektu. Dane są traktowane jako tablicę bajtów, dzięki czemu Wizualizator typów do manipulowania je w sposób, który jest wymagany do zaprezentowania użytkownikowi.  
  
 Przeglądarka niestandardowa umożliwia również tego interfejsu, jeśli to konieczne, chociaż zazwyczaj Przeglądarka niestandardowa wykorzystany niestandardowy interfejs [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) lub [GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md) (Aby uzyskać dane zorientowane na ciąg znaków).  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [Wizualizator typów i przeglądarka niestandardowa](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)

