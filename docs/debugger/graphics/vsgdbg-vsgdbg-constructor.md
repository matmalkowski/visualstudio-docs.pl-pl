---
title: VsgDbg::VsgDbg (Konstruktor) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 670651e6-5e79-4845-b0c2-671beb7055a8
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7231e0cc5c9d5946fabe504c16813ea47b24bdbc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="vsgdbgvsgdbg-constructor"></a>VsgDbg::VsgDbg (Konstruktor)
Tworzy wystąpienie klasy `VsgDbg` klasy z lub bez Przygotowywanie składnika w aplikacji diagnostyki grafiki aktywnie przechwytywanie i rejestrowanie informacji graficznych domyślnie na podstawie określonego parametru Boolean.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
VsgDbg(  
  bDefaultInit  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `bDefaultInit`  
 `true`Aby określić składników w aplikacji diagnostyki grafiki jest należy przygotować aktywnie przechwytywanie i rejestrowanie informacji graficznych; `false` Aby określić, że aplikacja nie powinna być przygotowana aktywnie przechwytywanie i rejestrowanie informacji graficznych w tej chwili.  
  
## <a name="remarks"></a>Uwagi  
 Podczas wywołania konstruktora z `bDefaultInit` ustawioną `true`, nazwa pliku w pliku dziennika grafiki zależy od sposobu `DONT_SAVE_VSGLOG_TO_TEMP` i `VSG_DEFAULT_RUN_FILENAME` symboli preprocesora są zdefiniowane przed `vsgcapture.h` znajduje się w aplikacji.  
  
 Podczas wywołania konstruktora z `bDefaultInit` ustawioną `false`, składnika diagnostyki grafiki w aplikacji można przygotować aktywnie przechwytywanie i rejestrowanie informacji graficznych w późniejszym czasie przez wywołanie metody `Init` funkcji.  
  
## <a name="see-also"></a>Zobacz też  
 [VsgDbg:: ~ VsgDbg (destruktor)](vsgdbg-tilde-vsgdbg-destructor.md)   
 [Init](init.md)   
 [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)   
 [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)