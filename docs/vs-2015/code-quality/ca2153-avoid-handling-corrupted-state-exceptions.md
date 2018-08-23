---
title: 'CA2153: Unikaj obsługiwania uszkodzonych wyjątków stanu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 418cc9cb-68ad-47e9-a6c8-a48b9c35db45
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 01a7b2ee185e60694dbfb286403f746d7754ef33
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42682357"
---
# <a name="ca2153-avoid-handling-corrupted-state-exceptions"></a>CA2153: Unikaj obsługiwania uszkodzonych wyjątków stanu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA2153: Unikaj obsługi uszkodzony stan wyjątki](https://docs.microsoft.com/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions).  
  
Element TypeName | AvoidHandlingCorruptedStateExceptions |  
| CheckId | CA2153 |  
| Kategoria | Microsoft.Security|  
| Zmiana powodująca niezgodność | Inne niż powodująca niezgodność |  
  
## <a name="cause"></a>Przyczyna  
 [Uszkodzony stan wyjątków (rozszerzenie klienta)](https://msdn.microsoft.com/magazine/dd419661.aspx) wskazać, że pamięć uszkodzenie istnieje w procesie. Przechwytywanie tych zamiast zezwalać awarię procesu może prowadzić do luk w zabezpieczeniach, jeśli osoba atakująca może wykorzystać do regionu pamięci uszkodzony.  
  
## <a name="rule-description"></a>Opis reguły  
 Rozszerzenie klienta wskazuje, że stan procesu został uszkodzony i nie zgłoszony przez system. W tym scenariuszu uszkodzony ogólny program obsługi tylko przechwytuje wyjątek po oznaczeniu metodę poprawne `HandleProcessCorruptedStateExceptions` atrybutu. Domyślnie [środowiska uruchomieniowego języka wspólnego (CLR)](https://msdn.microsoft.com/library/8bs2ecf4.aspx) nie wywoła obsługi catch w przypadku rozszerzeń klienta.  
  
 Zezwolenie na proces awarii bez wychwytywanie tych rodzajów wyjątków jest najbezpieczniejsza opcja, jako nawet rejestrowania kodu może umożliwić atakującemu wykorzystać błędy uszkodzenia pamięci.  
  
 To ostrzeżenie uaktywnia Przechwytywanie rozszerzeń klienta za pomocą ogólny program obsługi, który przechwytuje wszystkie wyjątki, takie jak catch(exception) ani catch (bez określenia wyjątków).  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby rozwiązać tego ostrzeżenia powinny wykonaj jedną z następujących czynności:  
  
 1. Usuń `HandleProcessCorruptedStateExceptions` atrybutu. Przywraca domyślne zachowanie środowiska uruchomieniowego, gdzie rozszerzeń klienta nie zostaną przekazane do obsługi catch.  
  
 2. Usuń procedurę obsługi catch ogólne, in preference of programów obsługi, które Przechwytuj typów wyjątków określonych.  Może to obejmować rozszerzeń klienta, przy założeniu, że kod procedury obsługi bezpiecznie mógł je obsłużyć (bardzo rzadko).  
  
 3. Ponowne generowanie rozszerzenie klienta w obsłudze catch, która zapewnia wyjątku jest przekazywany do obiektu wywołującego i spowoduje zakończenie uruchomionego procesu.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
## <a name="pseudo-code-example"></a>Przykładowy pseudo-kod  
  
### <a name="violation"></a>Naruszenie zasad  
 Poniższy pseudo-kod przedstawiono wzorzec wykryte przez tę regułę.  
  
```  
[HandleProcessCorruptedStateExceptions]   
//method to handle and log CSE exceptions   
void TestMethod1()   
{   
    try  
    {  
        FileStream fileStream = new FileStream("name", FileMode.Create);  
    }    
    catch (Exception e)  
    {  
        // Handle error  
    }  
}  
```  
  
### <a name="solution-1"></a>Rozwiązanie 1  
 Usuwanie atrybutu HandleProcessCorruptedExceptions gwarantuje, że wyjątki będą nie obsługiwane.  
  
```  
void TestMethod1()   
{   
    try  
    {  
        FileStream fileStream = new FileStream("name", FileMode.Create);  
    }    
    catch (IOException e)  
    {  
        // Handle error  
    }  
    catch (UnauthorizedAccessException e)  
    {  
        // Handle error  
    }  
}  
```  
  
### <a name="solution-2"></a>Rozwiązanie 2  
 Usuń procedurę obsługi catch ogólne i przechwytywać tylko typy określonego wyjątku.  
  
```  
void TestMethod1()   
{   
    try  
    {  
        FileStream fileStream = new FileStream("name", FileMode.Create);  
    }    
    catch (IOException e)  
    {  
        // Handle error  
    }  
    catch (UnauthorizedAccessException e)  
    {  
        // Handle error  
    }  
}  
```  
  
### <a name="solution-3"></a>Rozwiązanie 3  
 Ponownie zgłosić wyjątek.  
  
```  
void TestMethod1()   
{   
    try  
    {  
        FileStream fileStream = new FileStream("name", FileMode.Create);  
    }    
    catch (Exception e)  
    {  
        // Handle error  
        throw;  
    }  
}  
```



