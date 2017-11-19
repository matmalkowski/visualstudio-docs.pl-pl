---
title: IDebugPortSupplierDescription2 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugPortSupplierDescription2 interface
ms.assetid: dd19b9d6-0703-44b3-9498-cedffa0ce5b7
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8ce42039759128ac8b41556b94714da8cd43197d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugportsupplierdescription2"></a>IDebugPortSupplierDescription2
Umożliwia [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interfejsu użytkownika Służącego do wyświetlania tekstu wewnątrz **informacji transportu** sekcji **dołączyć do procesu** okno dialogowe.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugPortSupplierDescription2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Ten interfejs jest implementowany przez dostawców portu.  
  
## <a name="methods"></a>Metody  
 W poniższej tabeli przedstawiono metody `IDebugPortSupplierDescription2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)|Pobiera opis metadanych i Opis portu dostawcy.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll