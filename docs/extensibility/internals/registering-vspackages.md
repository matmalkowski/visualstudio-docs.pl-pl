---
title: Rejestrowanie VSPackages | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a6f7e603fbc023415ad2b8ddc157f239feb53768
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="registering-vspackages"></a>Rejestrowanie VSPackages
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zależy od plików .pkgdef do opisu i zlokalizuj pakiet VSPackage. Plik .pkgdef zawiera wszystkie informacje rejestracyjne, które w przeciwnym razie zostanie dodany do rejestru systemowego. Zarządzane VSPackages są rejestrowane przez dodanie atrybutów do kodu źródłowego, a następnie uruchamiając [elementu CreatePkgDef narzędzie](../../extensibility/internals/createpkgdef-utility.md) na zestaw wynikowy do wygenerowania pliku .pkgdef.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Określanie lokalizacji pliku pakietu VSPackage dla powłoki VS Shell](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)  
 Opisuje ścieżki ładowania VSPackages.  
  
 [Rejestrowanie i wyrejestrowywanie pakietów VSPackage](../../extensibility/registering-and-unregistering-vspackages.md)  
 Wyjaśniono, jak zarejestrować pakiet VSPackage.  
