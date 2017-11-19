---
title: IDiaSession::findInjectedSource | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSession::findInjectedSource method
ms.assetid: 907531b6-1ef8-4153-986d-b72611a1632d
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2dbac48aef894272d1edd9c4881c9f916255459b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idiasessionfindinjectedsource"></a>IDiaSession::findInjectedSource
Pobiera listę źródeł, który został umieszczony w magazynie symboli przez dostawców atrybut lub innych części procesu kompilacji.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT findInjectedSource (   
   LPCOLESTR                 srcFile,  
   IDiaEnumInjectedSources** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 srcFile  
 [in] Nazwa pliku źródłowego do wyszukania.  
  
 ppResult  
 [out] Zwraca [idiaenuminjectedsources —](../../debugger/debug-interface-access/idiaenuminjectedsources.md) obiekt, który zawiera listę wszystkich źródeł wprowadzony.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiaenuminjectedsources —](../../debugger/debug-interface-access/idiaenuminjectedsources.md)   
 [Idiasession —](../../debugger/debug-interface-access/idiasession.md)