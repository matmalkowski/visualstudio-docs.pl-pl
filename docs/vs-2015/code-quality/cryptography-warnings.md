---
title: Ostrzeżenia dotyczące kryptografii | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d96723ea-a293-488d-b9db-adb437e50cdd
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 947721de606cb6117ed2fd5f84bbc51e20e08203
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42697049"
---
# <a name="cryptography-warnings"></a>Ostrzeżenia dotyczące kryptografii
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [ostrzeżenia dotyczące kryptografii](https://docs.microsoft.com/visualstudio/code-quality/cryptography-warnings).  
  
Ostrzeżenia dotyczące kryptografii obsługują bezpieczniejsze biblioteki i aplikacje przy użyciu poprawnego użycia kryptografii. Ostrzeżenia te pomagają zapobiec usterkom w zabezpieczeniach w programie. Przyczynę wyłączenia któregokolwiek z tych ostrzeżeń należy wyraźnie oznaczyć w kodzie i poinformować o tym osobę odpowiedzialną za bezpieczeństwo w projekcie.  
  
|Reguła|Opis|  
|----------|-----------------|  
|[CA5350: Nie używaj słabych algorytmów kryptograficznych](../code-quality/ca5350-do-not-use-weak-cryptographic-algorithms.md)|Słabe szyfrowanie, algorytmy i funkcje wyznaczania wartości skrótu są używane obecnie do szeregu przyczyn, ale nie powinny być używane, aby zagwarantować poufność ani spójność danych, które chronią.        Ta zasada wyzwala, gdy znajdzie TripleDES, SHA1 lub RIPEMD160 algorytmów w kodzie.|  
|[CA5351: Nie używaj uszkodzonych algorytmów kryptograficznych](../code-quality/ca5351-do-not-use-broken-cryptographic-algorithms.md)|Uszkodzony kryptograficznych algorytmy nie są uznawane za bezpieczne i ich użycie powinno być zdecydowanie odradzane. Ta zasada wyzwala, gdy znajdzie algorytmu wyznaczania wartości skrótu MD5 lub DES lub RC2 algorytmów szyfrowania w kodzie.|



