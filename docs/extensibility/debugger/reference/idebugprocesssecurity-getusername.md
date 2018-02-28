---
title: IDebugProcessSecurity::GetUserName | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: aa8da8828dbbc314ce976572d1f6bd9d5abf5721
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprocesssecuritygetusername"></a>IDebugProcessSecurity::GetUserName
Pobiera nazwę użytkownika od dostawcy portu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetUserName(  
    BSTR *pbstrUserName  
);  
```  
  
```csharp  
int GetUserName (  
    string pbstrUserName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbstrUserName`  
 [out] Ciąg zawierający nazwę użytkownika.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwraca `S_OK`. W przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 `GetUserName`Zwraca nazwę użytkownika, który jest wyświetlany w **nazwy użytkownika** kolumny **dołączyć do procesu** okno dialogowe. Aby wyświetlić **dołączyć do procesu** okno dialogowe, kliknij przycisk **dołączyć do procesu** na **narzędzia** w menu [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] zintegrowane środowisko programistyczne (IDE).  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)