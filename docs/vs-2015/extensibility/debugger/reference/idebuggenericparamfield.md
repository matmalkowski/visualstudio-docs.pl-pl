---
title: IDebugGenericParamField | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugGenericParamField interface
ms.assetid: ba24f499-5ba7-4c67-83e6-923229b52327
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 841331b496aa21687a7ebdf90a6f4eee40b5ae89
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42682463"
---
# <a name="idebuggenericparamfield"></a>IDebugGenericParamField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [IDebugGenericParamField](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebuggenericparamfield).  
  
Reprezentuje parametr typu ogólnego kodu zarządzanego.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugGenericParamField : IDebugField  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Używane do obsługi typów ogólnych.  
  
## <a name="methods"></a>Metody  
 Oprócz metod na [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfejsu, ten interfejs implementuje następujące metody:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ConstraintCount](../../../extensibility/debugger/reference/idebuggenericparamfield-constraintcount.md)|Zwraca liczbę ograniczenia, które są skojarzone z tym parametru ogólnego.|  
|[GetConstraints](../../../extensibility/debugger/reference/idebuggenericparamfield-getconstraints.md)|Pobiera ograniczenia, które są skojarzone z tym parametru ogólnego.|  
|[Getflags —](../../../extensibility/debugger/reference/idebuggenericparamfield-getflags.md)|Pobranie flagi dla tego parametru ogólnego.|  
|[GetIndex](../../../extensibility/debugger/reference/idebuggenericparamfield-getindex.md)|Pobiera indeks tego parametru ogólnego.|  
|[GetNameOfFormalParam](../../../extensibility/debugger/reference/idebuggenericparamfield-getnameofformalparam.md)|Pobiera nazwę tego parametru ogólnego.|  
|[GetOwner —](../../../extensibility/debugger/reference/idebuggenericparamfield-getowner.md)|Pobiera właściciela tego parametru ogólnego typu lub metody.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

