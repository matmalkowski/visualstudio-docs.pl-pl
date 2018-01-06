---
title: IDebugSymbolProvider::GetTypeByName | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugSymbolProvider::GetTypeByName
helpviewer_keywords: IDebugSymbolProvider::GetTypeByName method
ms.assetid: b9d88d3b-8b75-484a-b9cc-dc8c0fbb4bc8
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 02ebe899354c0b9e98aa15adb9a59273fa9ff8cd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugsymbolprovidergettypebyname"></a>IDebugSymbolProvider::GetTypeByName
Ta metoda mapuje nazwę symbolu na typ symbolu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetTypeByName(   
   LPCOLESTR     pszClassName,  
   NAME_MATCH    nameMatch,  
   IDebugField** ppField  
);  
```  
  
```csharp  
int GetTypeByName(  
   string          pszClassName,   
   NAME_MATCH      nameMatch,   
   out IDebugField ppField  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszClassName`  
 [in] Nazwa symbolu.  
  
 `nameMatch`  
 [in] Wybiera typ dopasowania, na przykład, z uwzględnieniem wielkości liter. Wartość z zakresu od [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) wyliczenia.  
  
 `ppField`  
 [out] Zwraca typ symbolu jako [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Tej metody jest rodzajowy wersja [GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md).  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)   
 [GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)