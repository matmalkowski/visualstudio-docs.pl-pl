---
title: "Długość tablicy musi być skończony dodatnią liczbą całkowitą | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5029
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1a467040-4702-4178-848f-418a5974e907
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c6589bd2e9bb4acbec5f169087a49e64417dfae7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="array-length-must-be-a-finite-positive-integer"></a>Długość tablicy musi być skończony dodatnią liczbą całkowitą
Wywołujesz **tablicy** konstruktora z argumentem, który nie jest liczbą całkowitą (liczby całkowite składają się z zero plus zbiór dodatnie liczby całkowite).  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Użyj dodatnie liczby całkowite, tylko w przypadku tworzenia nowego `Array` obiektu. Jeśli chcesz utworzyć tablicy z pojedynczym elementem, który nie jest liczbą całkowitą, należy to zrobić w dwóch etapach. Najpierw utworzyć tablicy o jeden element, a następnie umieść wartość w pierwszym elemencie (array[0]). Poniżej znajduje się przykład tego błędu.  
  
    ```JavaScript  
    var piArray = new Array(3.14159);  
    ```  
  
     W poniższym przykładzie pokazano poprawne sposobem określania tablicy z pojedynczym elementem liczbowych.  
  
    ```JavaScript  
    var piArray = new Array(1);  
    piArray [0] = 3.14159;  
    ```  
  
     Nie ma żadnego górnego limitu rozmiaru tablicy, innego niż wartość maksymalna liczba całkowita (około miliarda 4).  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie tablic](../../javascript/advanced/using-arrays-javascript.md)