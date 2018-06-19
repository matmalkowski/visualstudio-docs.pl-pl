---
title: Winrterror — obiekt (JavaScript) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- WinRTError object [JavaScript]
- JavaScript, WinRTError object
ms.assetid: d75ab8e5-e729-4d86-90fd-ea228c30dd66
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 11b339b4fc3c4bd4f34416ffd98b8f9c3f288f98
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791779"
---
# <a name="winrterror-object-javascript"></a>WinRTError — Obiekt (JavaScript)
Po powrocie z wywołania środowiska wykonawczego systemu Windows HRESULT, która wskazuje błąd JavaScript konwertuje ją na specjalnych błąd środowiska uruchomieniowego systemu Windows. Jest dostępna tylko w [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] aplikacji, gdy środowisko wykonawcze systemu Windows jest dostępna, jako część globalnej przestrzeni nazw JavaScript.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
errorObj = new WinRTError();  
  
```  
  
## <a name="remarks"></a>Uwagi  
 Winrterror — błąd typ jest używany tylko w przypadku błędów, które pochodzą z interfejsów API środowiska wykonawczego systemu Windows.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak zgłoszony i przechwycony winrterror —.  
  
```JavaScript  
try {  
            Windows.Storage.ApplicationData.localFolder.createFileAsync("sample.txt");  
        } catch (err) {  
            var n = err;  
        }  
  
```  
  
## <a name="methods"></a>Metody  
 Winrterror — obiekt nie ma żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Winrterror — obiekt ma takie same właściwości jako [obiektu Error](../../javascript/reference/error-object-javascript.md) obiektu.  
  
## <a name="requirements"></a>Wymagania  
 Winrterror — obiekt jest obsługiwany tylko [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] aplikacji, a nie w programie Internet Explorer.  
  
## <a name="see-also"></a>Zobacz też  
 [Error — obiekt](../../javascript/reference/error-object-javascript.md)