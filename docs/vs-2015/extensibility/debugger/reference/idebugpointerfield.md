---
title: IDebugPointerField | Dokumentacja firmy Microsoft
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
- IDebugPointerField
helpviewer_keywords:
- IDebugPointerField interface
ms.assetid: d51bd5b2-f18e-4e27-b4fb-e6f652fbf635
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e8dd3e0a817de4b86bc6fae83bcdfa88d510c953
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42684900"
---
# <a name="idebugpointerfield"></a>IDebugPointerField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [IDebugPointerField](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugpointerfield).  
  
Ten interfejs reprezentuje typ wskaźnika.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugPointerField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Dostawca symboli implementuje ten interfejs do reprezentacji wskaźnika.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Użyj [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) uzyskać ten interfejs z [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfejsu, jeśli [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) zwraca `FIELD_TYPE_POINTER`.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 Oprócz metod na `IDebugField` i `IDebugContainerField` interfejsów, ten interfejs implementuje następującą metodę:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetDereferencedField](../../../extensibility/debugger/reference/idebugpointerfield-getdereferencedfield.md)|Zwraca [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) opisującej cel wskaźnika.|  
  
## <a name="remarks"></a>Uwagi  
 W języku C/C++ wskaźnik może mieć kontener, jeśli jest on używany w tablicy notacji. Na przykład, biorąc pod uwagę `char *pString`, `pString` ma typ wskaźnika do `char`. `pString[3]` Typ kontenera, który jest wskaźnikiem do `char` odwołujący się czwarty element tego kontenera.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy dostawca symboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)

