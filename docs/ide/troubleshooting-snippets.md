---
title: "Rozwiązywanie problemów z fragmentów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IntelliSense Code Snippets, troubleshooting
- troubleshooting IntelliSense Code Snippets
- troubleshooting Visual Basic, IntelliSense Code Snippets
ms.assetid: 7b6dd40e-2f78-4b50-8e68-41fac1bcb81e
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: bc17b237d2bd38d146a70fb05c1c4f6a91f98b37
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="troubleshooting-snippets"></a>Rozwiązywanie problemów z wstawkami kodu programu
Problemy z wstawki kodu IntelliSense są zazwyczaj spowodowane dwa problemy: uszkodzony fragment pliku lub Zła zawartość pliku fragment kodu.  
  
## <a name="common-problems"></a>Typowe problemy  
  
### <a name="the-snippet-cannot-be-dragged-from-file-explorer-to-a-visual-studio-source-file"></a>Fragment kodu nie mogą być przeciągnięte z Eksploratora plików do pliku źródłowego programu Visual Studio  
  
-   Kod XML w pliku fragment może być uszkodzony. **Edytora XML** w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] można zlokalizować problemów w strukturze XML.  
  
-   Fragment pliku może nie być zgodne ze schematem fragment kodu. **Edytora XML** w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] można zlokalizować problemów w strukturze XML.  
  
### <a name="the-code-has-compiler-errors-that-are-not-highlighted"></a>Kod ma błędy kompilatora, które nie są wyróżnione  
  
-   Być może brakuje odwołania projektu. Sprawdź dokumentację dotyczącą fragment kodu. Jeśli na komputerze nie znaleziono odwołania, należy go zainstalować. Wstawianie wstawek należy dodać do projektu wszystkie niezbędne odwołania. Jeśli informacje, które mogą być zgłaszane do twórcy fragment jako błąd Brak fragmentu.  
  
-   Zmienna może być niezdefiniowana. Niezdefiniowany zmiennych w fragment powinien być zaznaczony. Jeśli nie, które mogą być zgłaszane do twórcy fragment jako błąd.  
  
## <a name="see-also"></a>Zobacz też  
 [Fragmenty kodu](../ide/code-snippets.md)