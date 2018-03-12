---
title: "Wyłączenie debugera programu Visual Studio dla programu Windows Workflow Foundation (starsze) | Dokumentacja firmy Microsoft"
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- workflows, disabling debugger
- debugging workflows, disabling debugger
- workflow debugger, disabling
ms.assetid: 9da96d0e-f941-4fa9-a1a5-6bab50adfec9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d3ec3d87952f17feb8a59ae8acbda603451fbf4d
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2018
---
# <a name="disabling-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>Wyłączenie debugera programu Visual Studio dla programu Windows Workflow Foundation (starsze)

W tym temacie opisano sposób wyłączania [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] debugera przy użyciu pliku konfiguracji podczas kompilowania [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] aplikacji w Projektancie przepływów pracy starszej wersji systemu Windows. Użyj starszego [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] konieczność docelowy: [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] lub [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

 Domyślnie [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] debugera dla [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] jest włączona dla procesu hosta. Aby wyłączyć debugowanie przepływu pracy, musisz jawnie wyłączyć ją, dodając wpis "DisableWorkflowDebugging"  **\<przełączniki >** element  **\<system.diagnostics >**sekcji pliku konfiguracji hosta.

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