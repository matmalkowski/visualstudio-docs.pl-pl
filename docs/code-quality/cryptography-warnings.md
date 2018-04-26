---
title: Ostrzeżenia kryptografii
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: d96723ea-a293-488d-b9db-adb437e50cdd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d55d0d565db2287c51b6e1e96ac26aecad1be1fa
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="cryptography-warnings"></a>Ostrzeżenia kryptografii
Ostrzeżenia kryptografii obsługuje bezpieczniejsze bibliotek i aplikacji za pośrednictwem prawidłowe użycie kryptograficzne. Ostrzeżenia te pomagają zapobiec usterkom w zabezpieczeniach w programie. Przyczynę wyłączenia któregokolwiek z tych ostrzeżeń należy wyraźnie oznaczyć w kodzie i poinformować o tym osobę odpowiedzialną za bezpieczeństwo w projekcie.

|Reguła|Opis|
|----------|-----------------|
|[CA5350: Nie używaj słabych algorytmów kryptograficznych](../code-quality/ca5350-do-not-use-weak-cryptographic-algorithms.md)|Słabe algorytmy i funkcje skrótu są obecnie używane do istnieje wiele możliwych przyczyn, ale nie powinny być używane, aby zagwarantować poufność lub integralność danych, które chroni.        Ta zasada wyzwala, gdy znajdzie algorytmów TripleDES, SHA1 lub RIPEMD160 w kodzie.|
|[CA5351: Nie używaj uszkodzonych algorytmów kryptograficznych](../code-quality/ca5351-do-not-use-broken-cryptographic-algorithms.md)|Uszkodzony kryptograficznych algorytmy nie są uznawane za bezpieczne i ich użycia powinna być zdecydowanie niezalecane. Ta zasada wyzwala, gdy znajdzie algorytmu wyznaczania wartości skrótu MD5 lub algorytmów szyfrowania DES lub RC2 w kodzie.|