---
title: Idiasession::findinjectedsource — | Dokumentacja firmy Microsoft
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
- IDiaSession::findInjectedSource method
ms.assetid: 907531b6-1ef8-4153-986d-b72611a1632d
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 73f40f2536b72c900e20ff49492ff741e3ca927d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42685195"
---
# <a name="idiasessionfindinjectedsource"></a>IDiaSession::findInjectedSource
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [idiasession::findinjectedsource —](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasession-findinjectedsource).  
  
Pobiera listę źródeł, który został umieszczony w magazynie symboli przez atrybut dostawców lub innych części procesu kompilacji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT findInjectedSource (   
   LPCOLESTR                 srcFile,  
   IDiaEnumInjectedSources** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 srcFile  
 [in] Nazwa pliku źródłowego, który chcesz wyszukać.  
  
 ppResult  
 [out] Zwraca [idiaenuminjectedsources —](../../debugger/debug-interface-access/idiaenuminjectedsources.md) obiekt, który zawiera listę wszystkich źródeł wprowadzony.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiaenuminjectedsources —](../../debugger/debug-interface-access/idiaenuminjectedsources.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)



