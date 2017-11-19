---
title: Kopiowanie (przechwycenie programowe) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a0b8cb397afd4f1ba58dca30b4314471b4647576
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="copy-programmatic-capture"></a>Kopiowanie (przechwycenie programowe)
Kopiuje zawartość pliku dziennika (.vsglog) Grafika aktywna do nowego pliku.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
void Copy(  
  wchar_t const * szNewVSGLog  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `szNewVSGLog`  
 Nazwa pliku nowy plik dziennika grafiki.  
  
## <a name="remarks"></a>Uwagi  
 Aby skopiować informacji graficznych do nowego pliku, muszą już przechwycone niektórych informacji graficznych; w przeciwnym razie nic się nie dzieje.