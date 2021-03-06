---
title: Rozwiązywanie problemów z fragmentów kodu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IntelliSense Code Snippets, troubleshooting
- troubleshooting IntelliSense Code Snippets
- troubleshooting Visual Basic, IntelliSense Code Snippets
ms.assetid: 7b6dd40e-2f78-4b50-8e68-41fac1bcb81e
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a6cc8cde833d9580e3fae03df2df11e87eed8cf2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42684069"
---
# <a name="troubleshooting-snippets"></a>Rozwiązywanie problemów z wstawkami kodu programu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [Rozwiązywanie problemów z fragmentów](https://docs.microsoft.com/visualstudio/ide/troubleshooting-snippets).  
  
Problemy z fragmenty kodu IntelliSense są zazwyczaj spowodowane dwa problemy: plik fragmentu w uszkodzona lub zły zawartość pliku fragmentu kodu.  
  
## <a name="common-problems"></a>Typowe problemy  
  
### <a name="the-snippet-cannot-be-dragged-from-file-explorer-to-a-visual-studio-source-file"></a>Fragment kodu nie można przeciągnąć z Eksploratora plików do pliku źródłowego programu Visual Studio  
  
-   Kod XML w pliku fragmentu kodu może być uszkodzony. **Edytora XML** w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] mogą zlokalizować problemów w strukturze XML.  
  
-   Plik fragmentu kodu nie może być zgodny ze schematem fragmentu kodu. **Edytora XML** w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] mogą zlokalizować problemów w strukturze XML.  
  
### <a name="the-code-has-compiler-errors-that-are-not-highlighted"></a>Kod ma błędy kompilatora, które nie są wyróżnione  
  
-   Być może brakuje odwołania projektu. Sprawdź dokumentację dotyczącą fragmentu kodu. Odwołanie nie zostanie znaleziony na komputerze, należy go zainstalować. Wstawianie fragmentu należy dodać do projektu wszystkie odwołania potrzebne. Jeżeli ten fragment kodu brakuje zawiera informacje, które mogą zostać zgłoszone do autora fragmentu kodu jako błąd.  
  
-   Zmienna może być niezdefiniowana. Powinien być wyróżniony niezdefiniowane zmienne we fragmencie. Jeśli nie, które mogą zostać zgłoszone do autora fragmentu kodu jako błąd.  
  
## <a name="see-also"></a>Zobacz też  
 [Fragmenty kodu](../ide/code-snippets.md)



