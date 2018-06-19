---
title: getUTCHours — metoda (Data) (JavaScript) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- getUTCHours
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- hours
- UTC times, returning
- getUTCHours method
ms.assetid: 7c9825dd-4b3a-4614-8e09-f40df123b630
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c47fe66e6eecb9e3aaa53f0d0988631062676d17
ms.sourcegitcommit: ba29e4d37db92ec784d4acf9c6e120cf0ea677e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2018
ms.locfileid: "28943852"
---
# <a name="getutchours-method-date-javascript"></a>getUTCHours — Metoda (Data) (JavaScript)
Pobiera wartość godziny w `Date` przy użyciu uniwersalnego czasu koordynowanego (UTC).  
  
## <a name="syntax"></a>Składnia  
  
```  
  
dateObj.getUTCHours()   
```  
  
#### <a name="parameters"></a>Parametry  
 Wymagane `dateObj` odwołanie jest `Date` obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca liczbę całkowitą od 0 do 23 wskazującą liczbę godzin od północy. Zero jest zwracany, gdy czas przed 1:00:00: 00. Jeśli `Date` obiekt został utworzony bez określania czasu, domyślnie godzinę wynosi 0 w formacie UTC. Ten czas może być różna od zera w innych strefach czasowych.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać liczbę godzin jaka upłynęła od północy przy użyciu czasu lokalnego, użyj `getHours` metody.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `getUTCHours` metody.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getUTCHours());  
document.write("<br/>");  
  
var date2 = new Date("1/1/2001 11:22:33");  
document.write(date2.getUTCHours());  
  
// Output (in the PST time zone):  
// 15 
// 2  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Dotyczy**: [obiekt Date](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [getHours — metoda (Data)](../../javascript/reference/gethours-method-date-javascript.md)   
 [setHours — metoda (Data)](../../javascript/reference/sethours-method-date-javascript.md)   
 [setUTCHours, metoda (Date)](../../javascript/reference/setutchours-method-date-javascript.md)
