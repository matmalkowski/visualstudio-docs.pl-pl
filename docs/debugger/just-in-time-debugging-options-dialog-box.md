---
title: Just-In-Time, debugowanie, opcje ― Okno dialogowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Debugger.JIT
- vs.debug.options.JIT
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Just-In-Time debugging, setting options
- Options dialog box, debugging
ms.assetid: 7f11b2e3-3fb5-449d-b07c-6ecf1d6a487d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7be7dacbe7b3b89b8bdc09515c23d7597e7e55e5
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31480892"
---
# <a name="just-in-time-debugging-options-dialog-box"></a>Just-in-time, debugowanie, opcje ― Okno dialogowe
Aby uzyskać dostęp do **Just In Time** strony, przejdź do **narzędzia** menu i kliknij przycisk **opcje**. W **opcje** okna dialogowego rozwiń **debugowanie** a następnie wybierz węzeł **Just In Time**. Ta strona umożliwia włączenie debugowania kodu zarządzanego, kodu natywnego i skryptu Just In Time. Aby uzyskać więcej informacji, zobacz [debugowanie just in Time](../debugger/just-in-time-debugging-in-visual-studio.md).  
  
 Można włączyć debugowanie dla tych typów programów Just In Time:  
  
-   Zarządzane  
  
-   Natywne  
  
-   Skrypt  
  
 Debugowanie Just In Time to technika do debugowania program, który jest uruchamiany poza [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Można uruchomić programu, który został utworzony w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] poza [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] środowiska. Włączenie debugowania Just in time awarii wyświetli okno dialogowe z pytaniem do debugowania.  
  
## <a name="associated-warnings"></a>Ostrzeżenia skojarzony  
 Podczas odwiedzania tej strony w **opcje** okno dialogowe, można napotkać komunikat ostrzegawczy następująco:  
  
 **Inny debuger zarejestrował się jako Just-In-Time debugera. Aby naprawić, Włącz Just-In-Time debugowania lub uruchom naprawę Visual Studio.**  
  
 Ten komunikat występuje, gdy inny debuger, prawdopodobnie starszą wersję programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] debuger Just In Time w określonych debugera.  
  
 Inny komunikat, który może być wyświetlana jest następująca:  
  
 **W czasie wykryto debugowania błędy rejestracji. Aby naprawić, Włącz Just-In-Time debugowania lub uruchom naprawę Visual Studio.**  
  
 Jeśli zostanie wyświetlony jeden z tych ostrzeżeń, debugowanie za pomocą Just In Time [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] wymaga uprawnień administratora, dopóki problem został rozwiązany. Jeśli spróbujesz się po prostu włącz — jako bez uprawnień administratora w tych warunkach, zobaczysz komunikat o błędzie:  
  
 **Odmowa dostępu. Masz administratora Włącz Just In Time debugowanie lub napraw instalację programu Visual Studio.**  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie, opcje — Okno dialogowe](../debugger/debugging-options-dialog-box.md)   
 [Porady: Określanie ustawień debugera](../debugger/how-to-specify-debugger-settings.md)