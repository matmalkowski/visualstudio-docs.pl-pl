---
title: Rozwiązywanie problemów z wstawki kodu programu
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: troubleshooting
helpviewer_keywords:
- IntelliSense Code Snippets, troubleshooting
- troubleshooting IntelliSense Code Snippets
- troubleshooting Visual Basic, IntelliSense Code Snippets
ms.assetid: 7b6dd40e-2f78-4b50-8e68-41fac1bcb81e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dea93f5c575afc96af188ab2e92e2ee12b929549
ms.sourcegitcommit: 04a717340b4ab4efc82945fbb25dfe58add2ee4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="troubleshoot-snippets"></a>Rozwiązywanie problemów z wstawki kodu programu

Problemy z wstawki kodu IntelliSense są zazwyczaj spowodowane dwa problemy: uszkodzony fragment pliku lub Zła zawartość pliku fragment kodu.

## <a name="the-snippet-cannot-be-dragged-from-file-explorer-to-a-visual-studio-source-file"></a>Fragment kodu nie mogą być przeciągnięte z Eksploratora plików do pliku źródłowego programu Visual Studio

-   Kod XML w pliku fragment może być uszkodzony. **Edytora XML** w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] można zlokalizować problemów w strukturze XML.

-   Fragment pliku może nie być zgodne ze schematem fragment kodu. **Edytora XML** w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] można zlokalizować problemów w strukturze XML.

## <a name="the-code-has-compiler-errors-that-are-not-highlighted"></a>Kod ma błędy kompilatora, które nie są wyróżnione

-   Być może brakuje odwołania projektu. Sprawdź dokumentację dotyczącą fragment kodu. Jeśli na komputerze nie znaleziono odwołania, należy go zainstalować. Wstawianie wstawek należy dodać do projektu wszystkie niezbędne odwołania. Jeśli informacje, które mogą być zgłaszane do twórcy fragment jako błąd Brak fragmentu.

-   Zmienna może być niezdefiniowana. Niezdefiniowany zmiennych w fragment powinien być zaznaczony. Jeśli nie, które mogą być zgłaszane do twórcy fragment jako błąd.

## <a name="see-also"></a>Zobacz także

- [Fragmenty kodu](../ide/code-snippets.md)
