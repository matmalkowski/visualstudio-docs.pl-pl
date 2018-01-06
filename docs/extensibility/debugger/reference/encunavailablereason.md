---
title: EncUnavailableReason | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: EncUnavailableReason
helpviewer_keywords: EncUnavailableReason enumeration
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c057b01c07bd3a2ae9466dc394676fe553fe14d0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="encunavailablereason"></a>EncUnavailableReason
`This is for internal use only!`Reprezentuje przyczyn który **Edytuj i Kontynuuj** nie jest dostępna.  
  
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
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)   
 [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)