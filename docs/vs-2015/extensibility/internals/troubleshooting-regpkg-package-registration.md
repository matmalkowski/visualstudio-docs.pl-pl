---
title: Rozwiązywanie problemów z rejestracją pakietu RegPkg | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c5b2ebc470d12586957d77bbe7b076c053567742
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42686789"
---
# <a name="troubleshooting-regpkg-package-registration"></a>Rozwiązywanie problemów z rejestracją pakietu RegPkg
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [Rozwiązywanie problemów z rejestracji pakietu RegPkg](https://docs.microsoft.com/visualstudio/extensibility/internals/troubleshooting-regpkg-package-registration).  
  
> [!NOTE]
>  Jest preferowanym sposobem rejestrowanie pakietów w programie Visual Studio przy użyciu plików .pkgdef. Pozwala to na rozszerzenie wdrożenia bez potrzeby uzyskania dostępu do rejestru systemu. Pkgdef pliki są tworzone za pomocą [narzędzie CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md).  
  
 Aby zarejestrować pakiet za pomocą RegPkg w [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], należy użyć wersji RegPkg, który jest odpowiedni dla Twojego pakietu.  
  
## <a name="regpkg-versions-related-to-package-versions"></a>Wersje RegPkg związane z wersji pakietu  
 Istnieją dwie wersje RegPkg. Wersja jednego jest zawarta w [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Ta wersja umożliwia rejestrowanie pakietów, które zostały skompilowane przy użyciu jednej z następujących zestawów:  
  
1.  Microsoft.VisualStudioShell.9.0.dll  
  
2.  Microsoft.VisualStudioShell.10.0.dll  
  
3.  Microsoft.VisualStudioShell.11.0.dll  
  
 Go nie można zarejestrować pakiety, które zostały skompilowane przy użyciu starszych zestawu Microsoft.VisualStudio.Shell.dll.  
  
 Starszą wersję RegPkg można zarejestrować pakiety, które zostały skompilowane przy użyciu zestawu Microsoft.VisualStudio.Shell.dll. Jednak nie można go zarejestrować pakiety skompilowane przy użyciu nowszej wersji tego zestawu.  
  
## <a name="see-also"></a>Zobacz też  
 [Zwalnianie produktu](../../misc/releasing-a-visual-studio-integration-product.md)

