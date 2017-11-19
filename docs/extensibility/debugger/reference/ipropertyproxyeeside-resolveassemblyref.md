---
title: IPropertyProxyEESide::ResolveAssemblyRef | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IPropertyProxyEESide::ResolveAssemblyRef
helpviewer_keywords: IPropertyProxyEESide::ResolveAssemblyRef
ms.assetid: 662ca0a6-dad0-4c00-a718-bb3bbc5bd9da
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 730ee2eddcfd056ac664e1eb243e5e744aa1dafb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ipropertyproxyeesideresolveassemblyref"></a>IPropertyProxyEESide::ResolveAssemblyRef
Określa lokalizację odwołanie do określonego zestawu zarządzanego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT ResolveAssemblyRef(  
   BSTR*                  assemName,  
   IEEDataStorage**       assemBytes,  
   IEEDataStorage**       assemPdb,  
   BSTR*                  assemLocation,  
   ASSEMBLYLOCRESOLUTION* alr  
);  
```  
  
```csharp  
int ResolveAssemblyRef(  
   ref string                     assemName,  
   out IEEDataStorage             assemBytes,  
   out IEEDataStorage             assemPdb,  
   out string                     assemLocation,  
   out enum_ASSEMBLYLOCRESOLUTION alr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `assemName`  
 [in] Nazwa zestawu do rozpoznania.  
  
 `assemBytes`  
 [out] Zwraca [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) obiekt zawierający bajtów zestawu skojarzonego z odwołaniem.  
  
 `assemPdb`  
 [out] Zwraca `IEEDataStorage` obiektu zawierającego symbol są przechowywane dane skojarzone z tym odwołaniem.  
  
 `assemLocation`  
 [out] Zwraca ścieżkę lokalizacji tego odwołania.  
  
 `alr`  
 [out] Zwraca wartość z zakresu od [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md) Wyliczenie wskazujące lokalizacji zestawu tego odwołania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda nie jest zwykle implementowana przez ewaluatora wyrażenia niestandardowego.  
  
## <a name="see-also"></a>Zobacz też  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)