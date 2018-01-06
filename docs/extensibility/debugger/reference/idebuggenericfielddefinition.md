---
title: IDebugGenericFieldDefinition | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugGenericFieldDefinition interface
ms.assetid: b5a853b7-221e-4d62-8948-07423089d75d
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5ad51914225ddb8e6a558cac419d20119b286ab6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebuggenericfielddefinition"></a>IDebugGenericFieldDefinition
Reprezentuje definicję pola dla kodu zarządzanego typu ogólnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugGenericFieldDefinition : IUnknown  
```  
  
## <a name="methods"></a>Metody  
 Ten interfejs implementuje następujących metod:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ConstructInstantiation](../../../extensibility/debugger/reference/idebuggenericfielddefinition-constructinstantiation.md)|Tworzy wystąpienie pola podana tablica argumentów typu.|  
|[GetFormalTypeParams](../../../extensibility/debugger/reference/idebuggenericfielddefinition-getformaltypeparams.md)|Pobiera parametry typu podana liczba parametrów.|  
|[TypeParamCount](../../../extensibility/debugger/reference/idebuggenericfielddefinition-typeparamcount.md)|Pobiera liczbę skojarzony z polem ogólnych parametrów typu.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll