---
title: Idialoadcallback2::restrictoriginalpathaccess — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictOriginalPathAccess method
ms.assetid: 31fde3af-2824-4b0f-8d0d-cee6046596f6
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fb703ea0ffdab842e735a896c26066173943205e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42679739"
---
# <a name="idialoadcallback2restrictoriginalpathaccess"></a>IDiaLoadCallback2::RestrictOriginalPathAccess
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [idialoadcallback2::restrictoriginalpathaccess —](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idialoadcallback2-restrictoriginalpathaccess).  
  
Określa, czy można szukać pliku .pdb w oryginalny katalog debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT RestrictOriginalPathAccess ();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Dowolny kod powrotu innych niż `S_OK` zapobiega szuka pliku .pdb w oryginalny katalog debugowania. Oryginalny katalog debugowania jest ścieżką do pliku symboli, skompilowany do pliku wykonywalnego, jeśli debugowanie jest włączone. Ta ścieżka nie jest zawsze taki sam jak ścieżki, w którym znajduje się plik wykonywalny.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)



