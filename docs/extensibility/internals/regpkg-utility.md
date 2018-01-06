---
title: "Narzędzie RegPkg | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c4a4a3481b6ff1a5b8af0581e2c04602073adeae
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="regpkg-utility"></a>Narzędzie RegPkg
> [!NOTE]
>  Jest preferowany sposób rejestrowania pakietów w programie Visual Studio przy użyciu .pkgdef plików. Dzięki temu rozszerzenie wdrażania bez konieczności uzyskania dostępu do rejestru systemu, która jest wymagana do wdrożenia pliku VSIX. Pkgdef plików są tworzone za pomocą [elementu CreatePkgDef narzędzie](../../extensibility/internals/createpkgdef-utility.md). Aby uzyskać więcej informacji dotyczących wdrażania pakietu Visual Studio, zobacz [wysyłania rozszerzenia dla programu Visual Studio](../../extensibility/shipping-visual-studio-extensions.md).  
  
 Narzędzie RegPkg.exe rejestruje pakiet VSPackage z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] i przygotowuje go do wdrożenia. To narzędzie jest używane w tle podczas VSPackage programowania. Jest uruchamiana jako część procesu kompilacji, aby można skompilować i uruchomić pakiet VSPackage w gałęzi eksperymentalne.  
  
 RegPkg można wygenerować skryptów rejestru systemu w wielu formatach. Można zastosować te skrypty w projektach wdrożenia, takich jak projekty msi lub pliki zestaw narzędzi XML Instalatora Windows.  
  
 RegPkg.exe zazwyczaj znajduje się pod adresem \< *ścieżki instalacji programu Visual Studio SDK*> \VisualStudioIntegration\Tools\Bin\RegPkg.exe. RegPkg następujące następującej składni:  
  
```  
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath  
```  
  
 /Root:root  
 Przeprowadza rejestrację o określonej nazwie.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]katalog główny.  
  
 /RegFile:filename  
 Tworzy plik .reg, a nie aktualizacji rejestru.  Nie można używać z /vrgfile lub /rgsfile lub /wixfile.  
  
 /rgsfile:filename  
 Tworzy plik .rgs, a nie aktualizacji rejestru.  Nie można używać z /vrgfile lub/RegFile lub /wixfile.  
  
 /vrgfile:filename  
 Tworzy plik vrg, a nie aktualizacji rejestru.  Nie można używać z/RegFile lub /rgsfile lub /wixfile.  
  
 /rgm  
 Tworzy plik .rgm oprócz pliku rgs.  Musi być łączona z /rgsfile.  
  
 /wixfile:filename  
 Tworzy plik zgodny zestaw narzędzi XML Instalatora Windows, a nie aktualizacji rejestru.  Nie można używać z/RegFile lub /rgsfile lub /vrgfile.  
  
 /codebase  
 Wymusza rejestracji CodeBase zamiast zestawu.  
  
 / Assembly  
 Wymusza rejestrację przy użyciu zestawu niż CodeBase.  
  
 / unregister  
 Wyrejestrowuje tego pakietu.  Nie można użyć  
  
 / RegFile lub /vrgfile lub /rgsfile lub /wixfile.  
  
## <a name="see-also"></a>Zobacz też  
 [Pakiety VSPackage](../../extensibility/internals/vspackages.md)  
 [Rozwiązywanie problemów z rejestracją pakietu RegPkg](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)