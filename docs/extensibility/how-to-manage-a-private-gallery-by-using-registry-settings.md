---
title: "Porady: Zarządzanie galerii prywatnego za pomocą ustawień rejestru | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSIX private galleries, managing
- managing VSIX private galleries
ms.assetid: 86b86442-4293-4cad-9fe2-876eef65f426
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8d88c4b440f61e87792210e8a0844b6b622e8f05
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-manage-a-private-gallery-by-using-registry-settings"></a>Porady: Zarządzanie galerii prywatnego za pomocą ustawień rejestru
Jeśli jesteś administratorem lub deweloperem rozszerzenia Isolated Shell, można kontrolować dostęp do formantów, szablony i narzędzia w galerii programu Visual Studio, Galeria przykładów lub prywatnej galerii. Aby galerii dostępne lub niedostępne, należy utworzyć plik .pkgdef, który opisuje modyfikacji rejestru i ich wartości.  
  
## <a name="managing-private-galleries"></a>Zarządzanie galerie prywatnych  
 Można utworzyć plik .pkgdef kontrolować dostęp do galerii na wielu komputerach. Ten plik musi mieć następujący format.  
  
```  
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)  
Protocol=Atom Feed|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 `Repositories` Klucz odnosi się do galerii, aby włączyć lub wyłączyć. Galerii programu Visual Studio i galerii przykładów należy użyć następujących repozytorium identyfikatorów GUID:  
  
-   Galerii programu Visual Studio: 0F45E408-7995-4375-9485-86B8DB553DC9  
  
-   Przykłady galerii: AEB9CB40-D8E6-4615-B52C-27E307F8506C  
  
 `Disabled` Wartość jest opcjonalna. Galerii jest domyślnie włączone.  
  
 `Priority` Wartość określa kolejność, w którym Galerie są wyświetlane w oknie dialogowym Opcje. Galerii programu Visual Studio ma priorytet 10 i galerii przykładów ma priorytet 20. Uruchom prywatnej galerie priorytetem 100. Jeśli kilka Galerie mają taką samą wartość priorytetu, kolejność jest określana przez wartości ich zlokalizowanych `DisplayName` atrybutów.  
  
 `Protocol` Wartość jest wymagana do galerii na podstawie Atom lub oparty na programie SharePoint.  
  
 Albo `DisplayName`, lub obie `DisplayNameResourceID` i `DisplayNamePackageGuid`, musi być określona. Jeśli wszystkie są określone, a następnie `DisplayNameResourceID` i `DisplayNamePackageGuid` pary jest używany.  
  
## <a name="disabling-the-visual-studio-gallery-using-a-pkgdef-file"></a>Wyłączanie przy użyciu pliku .pkgdef galerii programu Visual Studio  
 Możesz wyłączyć galerii w pliku .pkgdef. Następujący wpis wyłącza galerii programu Visual Studio:  
  
```  
[$RootKey$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]  
"Disabled"=dword:00000001  
  
```  
  
 Następujący wpis wyłącza galerii przykładów:  
  
```  
[$RootKey$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]  
"Disabled"=dword:00000001  
  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Galerie prywatne](../extensibility/private-galleries.md)