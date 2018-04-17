---
title: IDebugEngine3::SetSymbolPath | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngine3::SetSymbolPath
helpviewer_keywords:
- IDebugEngine3::SetSymbolPath
ms.assetid: 47b48f84-8a96-401f-84df-0baa8a96d26e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d5a79cfd817be1a665f0008a39420e7cb39cc50b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="idebugengine3setsymbolpath"></a>IDebugEngine3::SetSymbolPath
Ustawia ścieżkę lub ścieżek, które są wyszukiwane symboli debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetSymbolPath (  
   LPOLESTR            szSymbolSearchPath,  
   LPOLESTR            szSymbolCachePath,  
   LOAD_SYMBOLS_FLAGS  Flags  
);  
```  
  
```csharp  
int SetSymbolPath(  
   string                    szSymbolSearchPath,   
   string                    szSymbolCachePath,   
   enum_LOAD_SYMBOLS_FLAGS   Flags  
);  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`szSymbolSearchPath`|[in] Ciąg zawierający ścieżki wyszukiwania symboli lub ścieżki. Aby uzyskać więcej informacji, zobacz "Uwagi". Nie może mieć wartości null.|  
|`szSymbolCachePath`|[in] Ciąg zawierający ścieżkę lokalną, gdzie mogą być buforowane symboli. Nie może mieć wartości null.|  
|`Flags`|[in] Nie jest używany; zawsze równa 0.|  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ciąg `szSymbolSearchPath` znajduje się lista co najmniej jedną ścieżkę, oddzielone średnikami, aby wyszukać symboli. Te ścieżki może być ścieżką lokalną, ścieżka UNC stylu lub adres URL. Tych ścieżek można też kombinacja różnych typów. Jeśli ścieżka jest ścieżką UNC (na przykład \\\Symserver\Symbols), a następnie aparat debugowania należy ustalić, czy ścieżka jest na serwerze symboli i powinno być możliwe załadowanie symboli z tego serwera, buforowanie ich w ścieżce określonej przez `szSymbolCachePath`.  
  
 Ścieżka symboli może również zawierać co najmniej jedna lokalizacja pamięci podręcznej. Pamięci podręczne są wymienione w kolejności priorytetu z pamięcią podręczną najwyższy priorytet najpierw i oddzielone * symboli. Na przykład:  
  
```  
\\symbols\symbols;\\someotherserver\symbols;c:\symbols\httpsymbols*http://msdl.microsoft.com  
```  
  
 [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md) metoda wykonuje rzeczywiste obciążenie symboli.  
  
## <a name="see-also"></a>Zobacz też  
 [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)   
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)