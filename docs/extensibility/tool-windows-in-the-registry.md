---
title: "Narzędzia systemu Windows w rejestrze | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tool windows, registering
ms.assetid: c4bb8add-7148-49e4-a377-01d059fd5524
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 8d3277a4e24b12d409654548b5670a4d47fa9539
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="tool-windows-in-the-registry"></a>Narzędzia systemu Windows w rejestrze
VSPackages, które zapewniają narzędzia windows należy zarejestrować się [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jako narzędzie dostawców okna. Narzędzie okien utworzone za pomocą szablonu pakietu Visual Studio w tym domyślnie. Narzędzie okno dostawców ma kluczy rejestru systemu, które określają atrybuty widoczność, takie jak domyślny rozmiar okna narzędzia i lokalizacji, identyfikator GUID okna, która służy jako okienko narzędzi i styl dokowania.  
  
 Podczas tworzenia dostawców okna narzędzia zarządzanych zarejestrować okna narzędzi dodawania atrybutów do kodu źródłowego, a następnie uruchamiając narzędzie RegPkg.exe na wynikowego zestawu. Aby uzyskać więcej informacji, zobacz [rejestrowanie okna narzędzia](../extensibility/registering-a-tool-window.md).  
  
## <a name="registering-unmanaged-tool-window-providers"></a>Podczas rejestrowania dostawców okna narzędzia niezarządzane  
 Dostawców okna narzędzi niezarządzane należy zarejestrować się [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] w sekcji ToolWindows rejestru systemu. Poniższy fragment pliku reg pokazuje, jak może być zarejestrowany dynamiczne okno:  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\<version number>\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}]  
@="{01069cdd-95ce-4620-ac21-ddff6c57f012}"  
"Name"="Microsoft.Samples.VisualStudio.IDE.ToolWindow.DynamicWindowPane"  
"Float"="250, 250, 410, 430"  
"DontForceCreate"=dword:00000001  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}\Visibility]  
"{f1536ef8-92ec-443c-9ed7-fdadf150da82}"=dword:00000000  
```  
  
 W pierwszym klucza w powyższym przykładzie, numer wersji jest wersja [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], takie jak w wersji 7.1 lub 8.0, podklucz {f0e1e9a1-9860-484d-ad5d-367d79aabf55} jest identyfikatorem GUID okienku okna narzędzia (DynamicWindowPane) i {wartość domyślną 01069cdd-95ce-4620-ac21-ddff6c57f012} jest identyfikatorem GUID pakiet VSPackage, zapewniając okna narzędzia. Opis podkluczy zmiennoprzecinkowych i DontForceCreate znaleźć [konfiguracji wyświetlania okna narzędzia](../extensibility/tool-window-display-configuration.md).  
  
 Drugi klucz opcjonalne ToolWindows\Visibility, określa identyfikatory GUID poleceń, które wymagają okna narzędzia, aby były widoczne. W tym przypadku są żadnych poleceń określony. Aby uzyskać więcej informacji, zobacz [konfiguracji wyświetlania okna narzędzia](../extensibility/tool-window-display-configuration.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Pakiety VSPackage](../extensibility/internals/vspackages.md)