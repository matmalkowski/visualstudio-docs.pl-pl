---
title: "IJsDebugDataTarget::AllocateVirtualMemory — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugDataTarget.AllocateVirtualMemory
apilocation: jscript9diag.dll
ms.assetid: 1d3a77b0-c1de-4a0c-a759-3e0c68fd96dd
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 65b29bbf9a3405bcfab779bd877f798a863538d5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugdatatargetallocatevirtualmemory-method"></a>IJsDebugDataTarget::AllocateVirtualMemory — Metoda
Rezerwuje i/lub zatwierdza obszaru pamięci w wirtualnej przestrzeni adresowej procesu docelowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT AllocateVirtualMemory(  
   UINT64 address,  
   DWORD size,  
   DWORD allocationType,  
   DWORD pageProtection,  
   UINT64 *pAllocatedAddress  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `address`  
 [in] Adres w ramach procesu docelowego, gdzie zatwierdzenia lub zarezerwowana pamięć. Ta wartość jest zazwyczaj zero, w których przypadku system wybierze adres.  
  
 `size`  
 [in] Rozmiar obszaru pamięci, aby przydzielić w bajtach. System zostanie automatycznie zaokrąglij w górę do następnej strony granicy.  
  
 `allocationType`  
 [in] Wskazuje typ alokacji do wykonania. Jest to zazwyczaj MEM_COMMIT &#124; MEM_RESERVE (0x3000), która rezerwuje i zatwierdza alokacji w jednym kroku.  
  
 `pageProtection`  
 [in] Ochrona pamięci dla regionu stron, które mają zostać przydzielone. Jeśli prace stron, można określić jedno stałych ochrony pamięci (na przykład PAGE_READWRITE, PAGE_EXECUTE).  
  
 `pAllocatedAddress`  
 [out] Adres podstawowy przydzielonego obszaru stron.  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="remarks"></a>Uwagi  
 Funkcja inicjuje pamięci, który go przydziela na wartość 0, chyba że używana jest MEM_RESET. Aby uzyskać dodatkowe informacje Zobacz VirtualAlloc Win32 API.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jscript9diag.h  
  
## <a name="see-also"></a>Zobacz też  
 [Ijsdebugdatatarget — interfejs](../../winscript/reference/ijsdebugdatatarget-interface.md)