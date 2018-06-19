---
title: Promise — obiekt (JavaScript) | Dokumentacja firmy Microsoft
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
ms.assetid: 358ad98b-f7fa-448c-9ee0-ef1e2a45e9c6
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 61e5611dd0d455c7e7b704777cc2341ca43a2404
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791698"
---
# <a name="promise-object-javascript"></a>Promise — obiekt (JavaScript)
Udostępnia mechanizm do planowania zadań do wykonania na wartość, która nie ma jeszcze obliczanej. Jest abstrakcję do zarządzania interakcji z interfejsów API asynchronicznego.  
  
## <a name="syntax"></a>Składnia  
  
```  
var promise = new Promise(function(resolve, reject) { ... });  
```  
  
#### <a name="parameters"></a>Parametry  
 `promise`  
 Wymagany. Nazwa zmiennej, do której przypisano promise.  
  
 `resolve`  
 Wymagany. Funkcja, która działa, aby wskazać, że Obietnica została pomyślnie ukończona.  
  
 `reject`  
 Opcjonalny. Funkcja, która działa w celu wskazania, że Obietnica zostało odrzucone z powodu błędu.  
  
## <a name="remarks"></a>Uwagi  
 Obietnicę albo należy wykonać z wartością lub musi zostać odrzucone z powodu. `then` Metody obiektu Promise jest uruchamiany, gdy promise jest ukończona lub odrzucone, cokolwiek nastąpi najpierw. Jeśli Obietnica zakończyło się powodzeniem, realizacja funkcji obsługi `then` uruchamia metody. Odrzucony Obietnica funkcji obsługi błędu `then` — metoda (lub `catch` metody) uruchamia.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób wywołania funkcji (`timeout`) zwracająca obietnicę. Program obsługi realizacji `then` metoda jest uruchamiana po 5000ms upłynie limit czasu.  
  
```JavaScript  
function timeout(duration) {  
    return new Promise(function(resolve, reject) {  
        setTimeout(resolve, duration);  
    });  
}  
  
// Note: This code uses arrow function syntax  
var m = timeout(5000).then(() => {  
    console.log("done!");  
})  
  
// Output (after 5 seconds):  
// done!  
```  
  
## <a name="example"></a>Przykład  
 Można również łańcucha wywołań `then` metody, jak pokazano w poniższym kodzie. Sam każdy program obsługi uzupełniania musi Zwróć obietnicę w celu obsługi łańcucha. W ten kod, który wywołuje takie same `timeout` funkcja zwraca pierwsze wywołanie w celu limit czasu po 1000 ms. Pierwsze wywołania programu obsługi zakończenia `timeout` ponownie, i zwraca ten promise po 2000 MS. Program obsługi jego ukończenia następnie zgłasza błąd. Błąd wywołania procedury obsługi `Promise.all`, która zwraca tylko wtedy, gdy oba wywołania do czasu zakończenia lub odrzucone.  
  
```JavaScript  
var p = timeout(1000).then(() => {  
    return timeout(2000);  
}).then(() => {  
    throw new Error("error");  
}).catch(err => {  
    return Promise.all([timeout(100), timeout(200)]);  
})  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="functions"></a>Funkcje  
 W poniższej tabeli opisano funkcje `Promise` obiektu.  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|[Promise.all — funkcja](../../javascript/reference/promise-all-function-promise.md)|Łączy dwa lub więcej ze zobowiązania i zwraca tylko po ukończeniu wszystkich ze zobowiązania określony lub został odrzucony.|  
|[Promise.race — funkcja](../../javascript/reference/promise-race-function-promise.md)|Tworzy nowe obietnicę, które zostaną rozwiązania lub Odrzuć o tej samej wartości wynik jako pierwszy obietnicę w celu rozwiązania lub odrzucić między przekazano argumentów.|  
|[Promise.Reject — funkcja](../../javascript/reference/promise-reject-function-promise.md)|Tworzy nowy promise odrzucone z wyników równą przekazano argument.|  
|[Promise.Resolve — funkcja](../../javascript/reference/promise-resolve-function-promise.md)|Tworzy nowy promise rozwiązany z wyników równą jej argument.|  
  
## <a name="methods"></a>Metody  
 W poniższej tabeli opisano metody `Promise` obiektu.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CATCH — metoda](../../javascript/reference/catch-method-promise.md)|Umożliwia określenie zadań do wykonania na odrzucenie obietnicę.|  
|[Następnie — metoda](../../javascript/reference/then-method-promise.md)|Umożliwia określenie zadań do wykonania na realizację obietnicę.|