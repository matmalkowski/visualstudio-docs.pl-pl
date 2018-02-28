---
title: IPropertyProxyEESide::GetManagedViewerCreationData | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
helpviewer_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
ms.assetid: c4eb4d60-8816-4d52-bc8d-dffd4f066499
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 53964947ac69cb9b4958bff0a8a6fd4ffa0a8afa
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ipropertyproxyeesidegetmanagedviewercreationdata"></a>IPropertyProxyEESide::GetManagedViewerCreationData
Pobiera informacje o podglądu dla tego typu właściwości, aby można było utworzyć wystąpienia tego podglądu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetManagedViewerCreationData(  
   BSTR*                  assemName,  
   IEEDataStorage**       assemBytes,  
   IEEDataStorage**       assemPdb,  
   BSTR*                  className,  
   ASSEMBLYLOCRESOLUTION* alr,  
   BOOL*                  replacementOk  
);  
```  
  
```csharp  
int GetManagedViewerCreationData(  
   out string                     assemName,  
   out IEEDataStorage             assemBytes,  
   out IEEDataStorage             assemPdb,  
   out string                     className,  
   out enum_ASSEMBLYLOCRESOLUTION alr,  
   out int                        replacementOk  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `assemName`  
 [out] Zwraca nazwę zestaw zawierający ten obiekt.  
  
 `assemBytes`  
 [out] Zwraca [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) obiekt zawierający bajtów zestawu tego obiektu (jest to wartość null, jeśli liczba dostępnych bajtów nie).  
  
 `assemPdb`  
 [out] Zwraca `IEEDataStorage` obiektu zawierającego symbol przechowywania informacji dla tego obiektu (jest to wartość null Jeśli nie magazynu symboli jest dostępna).  
  
 `className`  
 [out] Zwraca nazwę klasy zawierające ten obiekt.  
  
 `alr`  
 [out] Zwraca wartość z zakresu od [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md) Wyliczenie wskazujące lokalizacji zestawu.  
  
 `replacementOk`  
 [out] Zwraca wartość niezerową (`TRUE`) Jeśli wartość tego obiektu można zmieniać; zero (`FALSE`) Jeśli obiekt jest tylko do odczytu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest używana przez typ wizualizatorów można utworzyć wystąpienia zarządzanego podglądu.  
  
## <a name="see-also"></a>Zobacz też  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)