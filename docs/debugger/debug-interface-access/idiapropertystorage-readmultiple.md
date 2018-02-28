---
title: IDiaPropertyStorage::ReadMultiple | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadMultiple
ms.assetid: 6ccc9397-ce41-4f72-b261-72ac252cd4a5
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: ffa66117095ef73ac9d25ce8117431f03ba0ad57
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idiapropertystoragereadmultiple"></a>IDiaPropertyStorage::ReadMultiple
Odczytuje określony właściwości z bieżącego zestawu właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT ReadMultiple(   
   ULONG          cpspec,  
   PROPSPEC const rgpspec,  
   PROPVARIANT    rgvar  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cpspec`  
 [in] Liczba właściwości określone w `rgpspec` tablicy. Jeśli zero, metoda zwraca właściwości, ale zwraca `S_OK` jako kod powodzenia.  
  
 `rgpspec`  
 [in] Tablica właściwości do odczytu. Właściwości można określić Identyfikatora właściwości lub nazwa opcjonalny ciąg. Nie jest konieczne określić właściwości w określonej kolejności w tablicy. Tablica może zawierać zduplikowanych właściwości, co w wartości właściwości zduplikowane zwrotu dla właściwości proste. Właściwości prosty nie powinien zwrócić odmowa dostępu podczas próby otwarcia ich po raz drugi. Tablica może zawierać mieszaninę identyfikatorów właściwości i identyfikatory ciągów. Ta tablica musi mieć co najmniej `cpspec` liczba wartości właściwości.  
  
 `rgvar`  
 [w, out] Tablica `PROPVARIANT` struktury (w przestrzeni nazw Microsoft.VisualStudio.OLE.Interop) wypełnia się wartości dla każdej właściwości. Tablica musi wynosić co najmniej `cpspec` elementy o rozmiarze. Obiekt wywołujący nie musi zainicjować wartości w tablicy.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli co najmniej jedna z właściwości nie został znaleziony. W przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli nie znaleziono właściwość, odpowiadający mu wpis w `rgvar` tablica zawiera `VARIANT` z typem `VT_EMPTY`.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)