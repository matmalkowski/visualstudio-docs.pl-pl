---
title: IDebugEngine3::SetSymbolPath | Dokumentacja firmy Microsoft
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
- IDebugEngine3::SetSymbolPath
helpviewer_keywords:
- IDebugEngine3::SetSymbolPath
ms.assetid: 47b48f84-8a96-401f-84df-0baa8a96d26e
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3d549f32963bcb43d68faaf8bcc0f60a25b1f102
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42680377"
---
# <a name="idebugengine3setsymbolpath"></a>IDebugEngine3::SetSymbolPath
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [IDebugEngine3::SetSymbolPath](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugengine3-setsymbolpath).  
  
Ustawia ścieżki lub ścieżek, które są przeszukiwane pod kątem symboli debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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
|`szSymbolSearchPath`|[in] Ciąg zawierający ścieżkę wyszukiwania symbolu lub ścieżki. Aby uzyskać szczegółowe informacje, zobacz "Uwagi". Nie może mieć wartości null.|  
|`szSymbolCachePath`|[in] Ciąg zawierający ścieżkę lokalną, gdzie symbole mogą być buforowane. Nie może mieć wartości null.|  
|`Flags`|[in] Nie jest używany; zawsze ustawiony na 0.|  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ciąg `szSymbolSearchPath` znajduje się lista jedną lub więcej ścieżek, oddzielając je średnikami do wyszukiwania symboli. Tych ścieżek może być ścieżką lokalną, ścieżka UNC stylu lub adresu URL. Te ścieżki mogą być także kombinacji różnych typów. Jeśli ścieżka UNC (na przykład \\\Symserver\Symbols), a następnie aparat debugowania należy ustalić, czy ścieżka do serwera symboli i powinno być możliwe załadować symbole z tego serwera, buforowanie ich w ścieżce określonej przez `szSymbolCachePath`.  
  
 Ścieżka symboli może również zawierać jedną lub więcej lokalizacji pamięci podręcznej. Pamięci podręczne są wymienione jako pierwsze w kolejności priorytetów z najwyższy priorytet pamięci podręcznej i oddzielone * symboli. Na przykład:  
  
```  
\\symbols\symbols;\\someotherserver\symbols;c:\symbols\httpsymbols*http://msdl.microsoft.com  
```  
  
 [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md) metoda przeprowadza rzeczywiste obciążenie symboli.  
  
## <a name="see-also"></a>Zobacz też  
 [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)   
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)

