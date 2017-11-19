---
title: Uruchamianie testu jednostkowego jako procesu 64-bitowego | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unit tests, creating
- unit tests, running
ms.assetid: d23a9ee7-58e3-4e8b-a38c-b2207ea73fea
caps.latest.revision: "25"
ms.author: douge
manager: douge
ms.openlocfilehash: bb22521dc0c4f4a1a824c3554ce37297a61108c5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="run-a-unit-test-as-a-64-bit-process"></a>Uruchamianie testu jednostkowego jako procesu 64-bitowego
Jeśli masz komputera 64-bitowego, można uruchomić testów jednostkowych i przechwytywanie informacji o pokryciu kodu jako proces 64-bitowy.  
  
## <a name="running-a-unit-test-as-a-64-bit-process"></a>Uruchamianie testu jednostkowego jako procesu 64-bitowego  
  
#### <a name="to-run-a-unit-test-as-a-64-bit-process"></a>Uruchamianie testu jednostkowego jako procesu 64-bitowego  
  
1.  Jeśli Twoje kodu lub testy zostały skompilowane jako 32-bitowy/x86, ale chcesz je uruchomić jako proces 64-bitowy, skompiluj ponownie, ich jako **Any CPU**, lub opcjonalnie jako **64-bitowych**.  
  
    > [!TIP]
    >  Maksymalna elastyczność należy skompilować projektów testów z **Any CPU** konfiguracji. Następnie możesz uruchomić na zarówno 32- i 64 bitowych agentów. Nie ma żadnych dodatkowych zalet kompilowanie projektów testów z **64-bitowych** konfiguracji.  
  
2.  Z menu programu Visual Studio wybierz **testu**, a następnie wybierz **ustawienia**, a następnie wybierz pozycję **architektury procesora**. Wybierz **x64** do uruchamiania testów jako procesu 64-bitowego.  
  
     \-lub -  
  
     Określ `<TargetPlatform>x64</TargetPlatform>` w pliku runsettings. Zaletą tej metody jest można określić grupy ustawień w różnych plikach i szybkie przełączanie się między innymi ustawieniami. Można również skopiować ustawienia między rozwiązaniami. Aby uzyskać więcej informacji, zobacz [Konfigurowanie testów jednostkowych przy użyciu pliku runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Uruchom testy jednostkowe za pomocą narzędzia Eksplorator testów](../test/run-unit-tests-with-test-explorer.md)   
 [Testowanie jednostek kodu](../test/unit-test-your-code.md)   
 [Określanie ustawień testu dla testów programu Visual Studio](/devops-test-docs/test/specifying-test-settings-for-visual-studio-tests)
