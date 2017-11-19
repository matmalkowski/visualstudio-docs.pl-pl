---
title: "Rozwiązywanie problemów z Rejestracja pakietu RegPkg | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c4a4162b91a9345c94b7bd6a7e2f1099da3d631e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="troubleshooting-regpkg-package-registration"></a>Rozwiązywanie problemów z RegPkg pakietu rejestracji
> [!NOTE]
>  Jest preferowany sposób rejestrowania pakietów w programie Visual Studio przy użyciu .pkgdef plików. Dzięki temu rozszerzenie wdrażania bez konieczności uzyskania dostępu do rejestru systemu. Pkgdef plików są tworzone za pomocą [elementu CreatePkgDef narzędzie](../../extensibility/internals/createpkgdef-utility.md).  
  
 Aby zarejestrować pakiet za pomocą RegPkg w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], należy użyć wersji RegPkg, który jest odpowiedni dla pakietu.  
  
## <a name="regpkg-versions-related-to-package-versions"></a>Wersje RegPkg związane z wersji pakietu  
 Istnieją dwie wersje RegPkg. Jedna wersja jest uwzględniona w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Użyj tej wersji, aby zarejestrować pakiety, które zostały utworzone przy użyciu jednej z następujących zestawów:  
  
1.  Microsoft.VisualStudioShell.9.0.dll  
  
2.  Microsoft.VisualStudioShell.10.0.dll  
  
3.  Microsoft.VisualStudioShell.11.0.dll  
  
 Nie można go zarejestrować pakiety, które zostały utworzone przy użyciu starszych zestawu Microsoft.VisualStudio.Shell.dll.  
  
 Starszą wersję RegPkg można zarejestrować pakiety, które zostały utworzone przy użyciu zestawu Microsoft.VisualStudio.Shell.dll. Jednak nie można go zarejestrować pakiety przy użyciu nowszej wersji tego zestawu.  
  
## <a name="see-also"></a>Zobacz też  
 [VSPackages](../../extensibility/internals/vspackages.md)