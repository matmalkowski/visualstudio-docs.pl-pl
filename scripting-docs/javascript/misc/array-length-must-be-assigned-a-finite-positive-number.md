---
title: Długość tablicy musi być przypisany dodatnią liczbę całkowitą | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5030
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: c51c66a4-a543-4e95-b18d-2cfbcb3d1fdd
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 63a9d714173334192028b9096de41968befa85ef
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24788884"
---
# <a name="array-length-must-be-assigned-a-finite-positive-number"></a>Długość tablicy musi być mieć przypisaną dodatnią liczbę całkowitą
Podczas ustawiania **długość** właściwości istniejącego **tablicy** , należy określić obiekt długość tablicy, która nie jest liczbą dodatnią lub zerem. Ten błąd występuje, gdy przypisanie wartości do **długość** właściwość `Array` obiekt, który ma wartość ujemną lub niebędące liczbą (`NaN`). Należy pamiętać, że [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] powoduje automatyczną konwersję liczbami ułamkowymi do całego liczb całkowitych.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Przypisz dodatnią liczbę całkowitą do właściwości length. Nie ma żadnego górnego limitu rozmiaru tablicy, innego niż wartość maksymalna liczba całkowita (około miliarda 4). W poniższym przykładzie pokazano prawidłowy sposób, aby ustawić **długość** właściwość **tablicy** obiektu.  
  
    ```JavaScript  
    var my_array = new Array();  
    my_array.length = 99;  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie tablic](../../javascript/advanced/using-arrays-javascript.md)