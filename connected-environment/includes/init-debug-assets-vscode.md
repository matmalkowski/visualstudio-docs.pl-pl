---
ms.topic: include
ms.openlocfilehash: dbf7482acb02c6347c9c0d0765ef962cfb43a050
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
## <a name="initialize-debug-assets-with-the-vs-code-extension"></a>Zainicjuj zasoby debugowania z rozszerzeniem kodzie VS
Najpierw należy skonfigurować naszych projektu kodu, aby kod VS będzie komunikować się z naszym środowisko projektowe na platformie Azure. Rozszerzenie kodzie VS połączone środowiska udostępnia polecenia pomocnika, aby ustawić konfigurację debugowania. 

Otwórz **palety polecenia** (przy użyciu **widok | Polecenie palety** menu) i użyj automatycznego zakończenia wpisz i wybierz polecenie: `Connected Environment: Create configuration files for connected development`. 

Spowoduje to dodanie konfiguracji debugowania dla środowiska połączone w obszarze `.vscode` folderu.

![](../media/vsce-command-palette.png)

> [!Note]
> **WAŻNE**: z powodu usterki, zamknij i ponownie otwórz kodzie VS przed kontynuowaniem.