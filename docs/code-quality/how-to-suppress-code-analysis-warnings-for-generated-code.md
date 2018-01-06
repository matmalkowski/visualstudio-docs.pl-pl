---
title: "Porady: pomijanie ostrzeżeń analizy kodu dla wygenerowanego kodu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: bd917c8c9a3b66dc1fe34e089e14481c2b7df5a5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>Porady: pomijanie ostrzeżeń analizy kodu dla wygenerowanego kodu
Kompilatory kodu zarządzanego często generowania kodu, który zostanie dodany do projektu ułatwia programowanie szybkie kodu. Ponadto deweloperzy często używać narzędzi innych firm ułatwia szybkie opracowywanie aplikacji. Narzędzia te również generować kod, który zostanie dodany do projektu.  
  
 Możesz wyświetlić naruszenia reguły, które wykrywa analizy kodu w wygenerowanym kodzie. Jednak nie można je wyświetlić, jeśli nie można wyświetlić i obsługa kodu, który zawiera naruszenie.  
  
 **Pomijaj wyniki z wygenerowanego kodu** pole wyboru na stronie właściwości analizy kodu projektu umożliwia wybranie, czy mają być wyświetlane ostrzeżenia analizy kodu z kod wygenerowany przez narzędzie innej firmy.  
  
> [!NOTE]
>  Ta opcja nie odrzuca kod — analiza błędów i ostrzeżeń z wygenerowanego kodu podczas błędy i ostrzeżenia są wyświetlane w formularzach i szablony. Jednocześnie można wyświetlać i obsługa kodu źródłowego dla formularza lub szablonu.  
  
### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>Aby pominąć ostrzeżeń dla wygenerowanego kodu w projekcie  
  
1.  Kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań, a następnie kliknij przycisk **właściwości**.  
  
2.  Kliknij przycisk **analiza kodu**.  
  
3.  Wybierz **Pomijaj wyniki z wygenerowanego kodu** pole wyboru.