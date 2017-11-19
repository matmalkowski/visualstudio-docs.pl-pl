---
title: "Ostrzeżenia kryptografii | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d96723ea-a293-488d-b9db-adb437e50cdd
caps.latest.revision: "7"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4936482aea909938e135e8f61164955dacc9e20b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="cryptography-warnings"></a>Ostrzeżenia kryptografii
Ostrzeżenia kryptografii obsługuje bezpieczniejsze bibliotek i aplikacji za pośrednictwem prawidłowe użycie kryptograficzne. Ostrzeżenia te pomagają zapobiec usterkom w zabezpieczeniach w programie. Przyczynę wyłączenia któregokolwiek z tych ostrzeżeń należy wyraźnie oznaczyć w kodzie i poinformować o tym osobę odpowiedzialną za bezpieczeństwo w projekcie.  
  
|Reguła|Opis|  
|----------|-----------------|  
|[CA5350: Nie używaj słabych algorytmów kryptograficznych](../code-quality/ca5350-do-not-use-weak-cryptographic-algorithms.md)|Słabe algorytmy i funkcje skrótu są obecnie używane do istnieje wiele możliwych przyczyn, ale nie powinny być używane, aby zagwarantować poufność lub integralność danych, które chroni.        Ta zasada wyzwala, gdy znajdzie algorytmów TripleDES, SHA1 lub RIPEMD160 w kodzie.|  
|[CA5351 Nie używaj przerwane algorytmy kryptograficzne](../code-quality/ca5351-do-not-use-broken-cryptographic-algorithms.md)|Uszkodzony kryptograficznych algorytmy nie są uznawane za bezpieczne i ich użycia powinna być zdecydowanie niezalecane. Ta zasada wyzwala, gdy znajdzie algorytmu wyznaczania wartości skrótu MD5 lub algorytmów szyfrowania DES lub RC2 w kodzie.|