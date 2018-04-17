---
title: EncUnavailableReason | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- EncUnavailableReason
helpviewer_keywords:
- EncUnavailableReason enumeration
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4dcf705015925145b790b14a44007fed8d8fad3b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="encunavailablereason"></a>EncUnavailableReason
`This is for internal use only!` Reprezentuje przyczyn który **Edytuj i Kontynuuj** nie jest dostępna.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum tagEncUnavailableReason {  
   ENCUN_NONE,  
   ENCUN_INTEROP,  
   ENCUN_SQLCLR,  
   ENCUN_MINIDUMP,  
   ENCUN_EMBEDDED,  
   ENCUN_ATTACH,  
   ENCUN_WIN64  
};  
typedef enum tagEncUnavailableReason EncUnavailableReason;  
```  
  
```csharp  
public enum EncUnavailableReason {  
   ENCUN_NONE,  
   ENCUN_INTEROP,  
   ENCUN_SQLCLR,  
   ENCUN_MINIDUMP,  
   ENCUN_EMBEDDED,  
   ENCUN_ATTACH,  
   ENCUN_WIN64  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 ENCUN_NONE  
 Nie przyczyny Dlaczego Edytuj i Kontynuuj nie jest dostępny.  
  
 ENCUN_INTEROP  
 Edytuj i Kontynuuj jest niedostępne podczas wywołania międzyoperacyjnego.  
  
 ENCUN_SQLCLR  
 Edytuj i Kontynuuj jest niedostępne podczas wywołania procedury SQL, która używa środowiska uruchomieniowego języka wspólnego (CLR).  
  
 ENCUN_MINIDUMP  
 Edytuj i Kontynuuj nie jest dostępna podczas przetwarzania mini zrzutu.  
  
 ENCUN_EMBEDDED  
 Edytuj i Kontynuuj jest niedostępny podczas przetwarzania osadzonego kodu.  
  
 ENCUN_ATTACH  
 Edytuj i Kontynuuj nie jest dostępna, ponieważ sesja został dołączony do, nie jest uruchamiane przez debuger.  
  
 ENCUN_WIN64  
 Edytuj i Kontynuuj nie jest dostępna podczas przetwarzania kodu 64-bitowego systemu Windows.  
  
## <a name="remarks"></a>Uwagi  
 To wyliczenie jest do użytku wewnętrznego tylko przez [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]. [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md) i [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md) zaimplementowanego przez dostawcę niestandardowego numeru portu należy zawsze zwracają `E_NOTIMPL`.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.idl  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)   
 [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)