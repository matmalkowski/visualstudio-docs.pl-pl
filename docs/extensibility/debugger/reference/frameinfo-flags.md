---
title: FRAMEINFO_FLAGS | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: FRAMEINFO_FLAGS
helpviewer_keywords: FRAMEINFO_FLAGS enumeration
ms.assetid: 41578062-8455-412a-9d8b-1e1e9dc8d52e
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e05d7471df151642f6495907694a0057ef39dfd4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="frameinfoflags"></a>FRAMEINFO_FLAGS
Określa informacje do pobrania dotyczące obiektu ramki stosu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_FRAMEINFO_FLAGS {  
   FIF_FUNCNAME              = 0x00000001,  
   FIF_RETURNTYPE            = 0x00000002,  
   FIF_ARGS                  = 0x00000004,  
   FIF_LANGUAGE              = 0x00000008,  
   FIF_MODULE                = 0x00000010,  
   FIF_STACKRANGE            = 0x00000020,  
   FIF_FRAME                 = 0x00000040,  
   FIF_DEBUGINFO             = 0x00000080,  
   FIF_STALECODE             = 0x00000100,  
   FIF_ANNOTATEDFRAME        = 0x00000200,  
   FIF_DEBUG_MODULEP         = 0x00000400,  
   FIF_FUNCNAME_FORMAT       = 0x00001000,  
   FIF_FUNCNAME_RETURNTYPE   = 0x00002000,  
   FIF_FUNCNAME_ARGS         = 0x00004000,  
   FIF_FUNCNAME_LANGUAGE     = 0x00008000,  
   FIF_FUNCNAME_MODULE       = 0x00010000,  
   FIF_FUNCNAME_LINES        = 0x00020000,  
   FIF_FUNCNAME_OFFSET       = 0x00040000,  
   FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,  
   FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,  
   FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,  
   FIF_FUNCNAME_ARGS_ALL     = 0x00700000,  
   FIF_ARGS_TYPES            = 0x01000000,  
   FIF_ARGS_NAMES            = 0x02000000,  
   FIF_ARGS_VALUES           = 0x04000000,  
   FIF_ARGS_ALL              = 0x07000000,  
   FIF_ARGS_NOFORMAT         = 0x08000000,  
   FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,  
   FIF_FILTER_NON_USER_CODE  = 0x20000000,  
   FIF_ARGS_NO_TOSTRING      = 0x40000000,  
   FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000  
};  
typedef DWORD FRAMEINFO_FLAGS;  
```  
  
```csharp  
public enum enum_FRAMEINFO_FLAGS {  
   FIF_FUNCNAME              = 0x00000001,  
   FIF_RETURNTYPE            = 0x00000002,  
   FIF_ARGS                  = 0x00000004,  
   FIF_LANGUAGE              = 0x00000008,  
   FIF_MODULE                = 0x00000010,  
   FIF_STACKRANGE            = 0x00000020,  
   FIF_FRAME                 = 0x00000040,  
   FIF_DEBUGINFO             = 0x00000080,  
   FIF_STALECODE             = 0x00000100,  
   FIF_ANNOTATEDFRAME        = 0x00000200,  
   FIF_DEBUG_MODULEP         = 0x00000400,  
   FIF_FUNCNAME_FORMAT       = 0x00001000,  
   FIF_FUNCNAME_RETURNTYPE   = 0x00002000,  
   FIF_FUNCNAME_ARGS         = 0x00004000,  
   FIF_FUNCNAME_LANGUAGE     = 0x00008000,  
   FIF_FUNCNAME_MODULE       = 0x00010000,  
   FIF_FUNCNAME_LINES        = 0x00020000,  
   FIF_FUNCNAME_OFFSET       = 0x00040000,  
   FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,  
   FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,  
   FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,  
   FIF_FUNCNAME_ARGS_ALL     = 0x00700000,  
   FIF_ARGS_TYPES            = 0x01000000,  
   FIF_ARGS_NAMES            = 0x02000000,  
   FIF_ARGS_VALUES           = 0x04000000,  
   FIF_ARGS_ALL              = 0x07000000,  
   FIF_ARGS_NOFORMAT         = 0x08000000,  
   FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,  
   FIF_FILTER_NON_USER_CODE  = 0x20000000,  
   FIF_ARGS_NO_TOSTRING      = 0x40000000,  
   FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 FIF_FUNCNAME  
 Inicjowanie użycia `m_bstrFuncName` pola.  
  
 FIF_RETURNTYPE  
 Inicjowanie użycia `m_bstrReturnType` pola.  
  
 FIF_ARGS  
 Inicjowanie użycia `m_bstrArgs` pola.  
  
 FIF_LANGUAGE  
 Inicjowanie użycia `m_bstrLanguage` pola.  
  
 FIF_MODULE  
 Inicjowanie użycia `m_bstrModule` pola.  
  
 FIF_STACKRANGE  
 Inicjowanie użycia `m_addrMin` i `m_addrMax` pola (stosu zakresu).  
  
 FIF_FRAME  
 Inicjowanie użycia `m_pFrame` pola.  
  
 FIF_DEBUGINFO  
 Inicjowanie użycia `m_fHasDebugInfo` pola.  
  
 FIF_STALECODE  
 Inicjowanie użycia `m_fStaleCode` pola.  
  
 FIF_ANNOTATEDFRAME  
 Inicjowanie użycia `m_fAnnotatedFrame` pola.  
  
 FIF_DEBUG_MODULEP  
 Inicjowanie użycia `m_pModule` pola.  
  
 FIF_FUNCNAME_FORMAT  
 Formatuje nazwę funkcji. Wynik jest zwracany w `m_bstrFunName` wypełnione pole i nie ma innych pól.  
  
 FIF_FUNCNAME_RETURNTYPE  
 Dodaje typ zwracany do `m_bstrFuncName` pola.  
  
 FIF_FUNCNAME_ARGS  
 Dodaje argumenty `m_bstrFuncName` pola.  
  
 FIF_FUNCNAME_LANGUAGE  
 Dodaje języka aby `m_bstrFuncName` pola.  
  
 FIF_FUNCNAME_MODULE  
 Nazwa modułu do dodaje `m_bstrFuncName` pola.  
  
 FIF_FUNCNAME_LINES  
 Dodaje liczba wierszy do `m_bstrFuncName` pola.  
  
 FIF_FUNCNAME_OFFSET  
 Dodaje do `m_bstrFuncName` pola przesunięcie w bajtach na początku wiersza, jeśli `FIF_FUNCNAME_LINES` jest określona. Jeśli `FIF_FUNCNAME_LINES` nie zostanie określony, lub jeśli numerów wierszy nie są dostępne, dodaje przesunięcie w bajtach od początku funkcji.  
  
 FIF_FUNCNAME_ARGS_TYPES  
 Dodaje typ argumentu funkcji do `m_bstrFuncName` pola.  
  
 FIF_FUNCNAME_ARGS_NAMES  
 Dodaje nazwę każdego argumentu funkcji `m_bstrFuncName` pola.  
  
 FIF_FUNCNAME_ARGS_VALUES  
 Dodaje wartość każdego argumentu funkcji `m_bstrFuncName` pola.  
  
 FIF_FUNCNAME_ARGS_ALL  
 Dodaje typ, nazwa i wartość wszystkich argumentów `m_bstrFuncName` pola.  
  
 FIF_ARGS_TYPES  
 Typy argumentów są pobierane i sformatowany.  
  
 FIF_ARGS_NAMES  
 Nazwy argumentu są pobierane i sformatowany.  
  
 FIF_ARGS_VALUES  
 Wartości argumentu są pobierane i sformatowany.  
  
 FIF_ARGS_ALL  
 Pobierz i sformatować typu, nazwy i wartości wszystkich argumentów.  
  
 FIF_ARGS_NOFORMAT  
 Określa, że argumenty nie są sformatowane (na przykład dodać otwierające i zamykające nawiasy listy argumentów nie Dodawanie separatora między argumentami).  
  
 FIF_ARGS_NO_FUNC_EVAL  
 Określa, że obliczanie funkcji (właściwość) nie powinna być używana podczas pobierania wartości argumentów.  
  
 FIF_FILTER_NON_USER_CODE  
 Aparat debugowania jest do filtrowania ramek kodu innych użytkowników, więc nie są uwzględniane.  
  
 FIF_ARGS_NO_TOSTRING  
 Nie zezwalaj na `ToString()` funkcji oceny lub formatowania, gdy zwracany jest argumenty funkcji.  
  
 FIF_DESIGN_TIME_EXPR_EVAL  
 Informacje ramki powinien zaakceptujesz z hostowanej domena aplikacji zamiast procesu hostingu.  
  
## <a name="remarks"></a>Uwagi  
 Te flagi są przekazywane do [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) i [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) metod, aby określić pola, które mają być inicjowane w [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) struktury lub struktury.  
  
 Te flagi są również używane w celu wskazania, które pola [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) struktury są używane i ważne, gdy struktura jest zwracany. Te wartości mogą być łączone z bitowego `OR`.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)