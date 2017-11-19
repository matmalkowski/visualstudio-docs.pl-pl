---
title: Rejestrowanie VSPackages | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2d580d3d74d8648b7181ac1ca384d3232fa8225b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="registering-vspackages"></a>Rejestrowanie VSPackages
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]zależy od plików .pkgdef do opisu i zlokalizuj pakiet VSPackage. Plik .pkgdef zawiera wszystkie informacje rejestracyjne, które w przeciwnym razie zostanie dodany do rejestru systemowego. Zarządzane VSPackages są rejestrowane przez dodanie atrybutów do kodu źródłowego, a następnie uruchamiając [elementu CreatePkgDef narzędzie](../../extensibility/internals/createpkgdef-utility.md) na zestaw wynikowy do wygenerowania pliku .pkgdef.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Określanie lokalizacji pliku pakiet VSPackage powłoki programu VS](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)  
 Opisuje ścieżki ładowania VSPackages.  
  
 [VSPackages rejestrowania i wyrejestrowywania](../../extensibility/registering-and-unregistering-vspackages.md)  
 Wyjaśniono, jak zarejestrować pakiet VSPackage.  
