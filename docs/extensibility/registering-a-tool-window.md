---
title: Rejestrowanie okna narzędzi | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, registering managed
- tool windows, registering
ms.assetid: 8c8c4a24-3da4-497b-9db2-0ddd7cfbfdd2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 17c9233d3df0bb7101b374fd1990536d2341fa49
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39638332"
---
# <a name="register-a-tool-window"></a>Rejestrowanie okna narzędzi
Możesz zarejestrować się przy użyciu narzędzia systemu windows <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> i <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute>.  
  
## <a name="example"></a>Przykład  
  
```csharp
  
[ProvideToolWindow(typeof(PersistedWindowPane), Style = MsVsShell.VsDockStyle.Tabbed, Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]
[ProvideToolWindow(typeof(DynamicWindowPane), PositionX=250, PositionY=250, Width=160, Height=180, Transient=true)]
[ProvideToolWindowVisibility(typeof(DynamicWindowPane), /*UICONTEXT_SolutionExists*/"f1536ef8-92ec-443c-9ed7-fdadf150da82")]  
[ProvideMenuResource(1000, 1)]  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("01069CDD-95CE-4620-AC21-DDFF6C57F012")]  
public class PackageToolWindow : Package  
{  
```
  
 W powyższym kodzie <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> rejestruje `PersistedWindowPane` i `DynamicWindowPane` narzędzia systemu windows z programem Visual Studio. Okno narzędzia utrwalonych jest zadokowany i z zakładkami z **Eksploratora rozwiązań**, i dynamiczne okno otrzymuje od położenia i rozmiaru domyślnego. Dynamiczne okna składa się błędem przejściowym, co oznacza, że nie jest tworzony podczas uruchamiania. Zapisuje to `DontForceCreate` wartość w `ToolWindows` klucza rejestru systemu. Aby uzyskać więcej informacji, zobacz [konfiguracji wyświetlania okna narzędzia](../extensibility/tool-window-display-configuration.md).
