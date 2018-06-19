---
title: Projektant przepływu pracy — wyłączanie debugera programu Visual Studio dla programu Windows Workflow Foundation (starsze)
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- workflows, disabling debugger
- debugging workflows, disabling debugger
- workflow debugger, disabling
ms.assetid: 9da96d0e-f941-4fa9-a1a5-6bab50adfec9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 473ee507e35f5ec5df902df64ee34326dcf90a2b
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31969968"
---
# <a name="disabling-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>Wyłączenie debugera programu Visual Studio dla programu Windows Workflow Foundation (starsze)

W tym temacie opisano, jak wyłączyć debuger programu Visual Studio przy użyciu pliku konfiguracji, podczas tworzenia aplikacji systemu Windows Workflow Foundation (WF) w starszej wersji projektanta przepływów pracy systemu Windows. Starsze projektanta przepływów pracy należy używać wtedy, gdy konieczne objęcie .NET Framework w wersji 3.5 lub WinFX.

 Domyślnie program Visual Studio Debugger dla Windows Workflow Foundation (WF) jest włączona dla procesu hosta. Aby wyłączyć debugowanie przepływu pracy, musisz jawnie wyłączyć ją, dodając wpis "DisableWorkflowDebugging"  **\<przełączniki >** element  **\<system.diagnostics >** sekcji pliku konfiguracji hosta.

 Poniższy przykład przedstawia sposób modyfikowania hosta pliku konfiguracji, aby wyłączyć debugowanie przepływu pracy.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
   <system.diagnostics>
      <switches>
         <add name="DisableWorkflowDebugging" value="true"/>
      </switches>
   </system.diagnostics>
</configuration>
```

## <a name="see-also"></a>Zobacz także

- [Wywoływanie debugera programu Visual Studio dla programu Windows Workflow Foundation (starsza wersja)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)
- [Debugowanie starszych wersji przepływów pracy](../workflow-designer/debugging-legacy-workflows.md)