---
title: Rejestrowanie pakietów VSPackage | Dokumentacja firmy Microsoft
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
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1c826b61e4f6d2255be7b7fdad967bab0d8dea74
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42693944"
---
# <a name="registering-vspackages"></a>Rejestrowanie pakietów VSPackage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [rejestrowanie pakietów VSPackage](https://docs.microsoft.com/visualstudio/extensibility/internals/registering-vspackages).  
  
[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] opiera się na plikach pkgdef do opisywania i zlokalizować pakietu VSPackage. Plik .pkgdef zawiera wszystkich informacji rejestracyjnych które w przeciwnym razie zostaną dodane do rejestru systemowego. Zarządzane pakietów VSPackage są rejestrowane przez dodawanie atrybutów do kodu źródłowego, a następnie uruchamiając [narzędzie CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md) w zestawie wynikowym, aby wygenerować plik .pkgdef.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Określanie lokalizacji pliku pakietu VSPackage dla powłoki VS Shell](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)  
 Opisuje ścieżkę ładowanie pakietów VSPackage.  
  
 [Rejestrowanie i wyrejestrowywanie pakietów VSPackage](../../extensibility/registering-and-unregistering-vspackages.md)  
 Wyjaśnia, jak zarejestrować pakietu VSPackage.  
  
 [Aby zarejestrować rozszerzenie za pomocą atrybutu niestandardowego rejestrowania](../../misc/using-a-custom-registration-attribute-to-register-an-extension.md)  
 W tym artykule opisano sposób tworzenia manifestu rejestracji, który może służyć do wdrażania zarządzanego pakietu VSPackage.

