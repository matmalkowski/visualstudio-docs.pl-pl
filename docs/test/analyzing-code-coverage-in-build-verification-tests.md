---
title: Analiza pokrycia kodu w testach weryfikacji kompilacji | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.author: gewarren
manager: ghogen
ms.workload: multiple
author: gewarren
ms.openlocfilehash: 3f02166c89837dfd122ab8a8c71913c659ab1dd2
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2018
---
# <a name="analyzing-code-coverage-in-build-verification-tests"></a>Analiza pokrycia kodu w testach weryfikacji kompilacji
Analizy pokrycia kodu w programie Microsoft Visual Studio zawiera, jaka część kodu jest są wykonywane przez testów automatycznych. Aby uzyskać więcej informacji, zobacz [przy użyciu pokrycia kodu do określenia, jaka część kodu jest poddawana testom](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).  
  
 Podczas sprawdzania kodu testy będą uruchamiane na serwerze kompilacji, razem z innymi testami pozostałych członków zespołu. (Jeśli nie zostało już skonfigurować tę funkcjonalność, zobacz [Uruchom testy w procesie budowy](http://msdn.microsoft.com/Library/d05743a1-c5cf-447e-bed9-bed3cb595e38).) Jest on przydatny do analizy pokrycia kodu w usłudze kompilacji, ponieważ zapewnia najbardziej aktualnych i kompleksowy obraz pokrycia w całego projektu. Zawiera również automatycznych testów systemowych i innych kodowane testy, które zwykle nie uruchamiane na komputerach programowanie.  
  
1.  W programie Team Explorer Otwórz **kompilacje**, a następnie dodaj lub Edytuj definicję kompilacji.  
  
2.  Na **procesu** rozwiń pozycję **testów automatycznych**, **źródła testu**, **parametrów uruchomieniowych**. Ustaw **typu pliku ustawień uruchamiania** do **włączonym pokryciem kodu**.  
  
     Jeśli masz więcej niż jedną definicję źródła testów, powtórz ten krok dla każdej z nich.  
  
    -   *Ale nie ma pola o nazwie **typu z Uruchom plik ustawień**.*  
  
         W obszarze **testów automatycznych**, wybierz pozycję **zestawu testowego** i kliknij przycisk wielokropka **[...]**  na końcu linii. W **Dodawanie/edytowanie testu** okna dialogowego, w obszarze **Test Runner**, wybierz **Visual Studio Test Runner**.  
  
 ![Ustawienie definicji kompilacji dla pokrycia kodu](../test/media/codecoverage-plaincc.png "CodeCoverage plainCC")  
  
 Po uruchomieniu kompilacji, wyniki pokrycia kodu jest wyświetlany w podsumowaniu kompilacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z pokrycia kodu do określania, jaka część kodu jest poddawana testom](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
