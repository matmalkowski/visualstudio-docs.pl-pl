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
ms.openlocfilehash: 80e5ba76a54b584e5eed74f507f1fb3b81e7f89e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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
 [Wstawki kodu](../ide/code-snippets.md)