---
title: Wykrywanie wymagania systemowe | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- setup, VSPackages
- launch conditions
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
caps.latest.revision: "50"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: dc16c51b72ced37072c4ddf6d47bf347cf57c0f8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="detecting-system-requirements"></a>Wykrywanie wymagania systemowe
Pakiet VSPackage nie może działać, chyba że jest zainstalowany program Visual Studio. Gdy Instalator systemu Microsoft Windows umożliwia zarządzanie instalacjami VSPackage, można skonfigurować Instalatora, aby wykryć, czy jest zainstalowany program Visual Studio. Można również skonfigurować go, aby sprawdzić systemu pod kątem innych wymagań, na przykład konkretnej wersji systemu Windows lub określonej ilości pamięci RAM.  
  
## <a name="detecting-visual-studio-editions"></a>Wykrywanie wersji programu Visual Studio  
 Aby ustalić, czy jest zainstalowana wersja programu Visual Studio, sprawdź wartość klucza rejestru instalacji (REG_DWORD) 1 w odpowiedni folder wymienione w poniższej tabeli. Należy pamiętać, że hierarchia wersje programu Visual Studio:  
  
1.  Enterprise  
  
2.  Professional Edition  
  
3.  Społeczność  
  
 "Wyżej" edition jest zainstalowany, dodawane są klucze rejestru, w przypadku tej wersji, a także jak w przypadku wersji "niżej". Oznacza to jeśli jest zainstalowany w wersji Enterprise, klucz instalacji jest równa 1 dla przedsiębiorstwa, a także w wersjach Professional oraz społeczność użytkowników. Dlatego należy sprawdzić tylko w przypadku wersji "najwyższy", które są potrzebne.  
  
> [!NOTE]
>  W 64-bitowej wersji Edytora rejestru, 32-bitowe klucze są wyświetlane w obszarze HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\\. Klucze Visual Studio podlegają HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\\.  
  
|Produkt|Key|  
|-------------|---------|  
|Visual Studio Enterprise 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\enterprise|  
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\professional|  
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\community|  
|Visual Studio 2015 Shell (zintegrowany i izolowany)|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell|  
  
## <a name="detecting-when-visual-studio-is-running"></a>Wykrywanie po uruchomieniu programu Visual Studio  
 Nie można zarejestrować poprawnie VSPackage, jeśli Visual Studio jest uruchomiony, gdy jest zainstalowany pakiet VSPackage. Instalator musi Wykryj, kiedy jest uruchomiony program Visual Studio i następnie odmówić zainstalować ten program. Instalator Windows nie umożliwia Użyj wpisów tabeli, aby włączyć wykrywanie takich modyfikacji. Zamiast tego utwórz akcji niestandardowej, w następujący sposób: Użyj `EnumProcesses` funkcji, aby wykryć procesu devenv.exe, a następnie ustaw właściwości Instalatora, który jest używany w warunek uruchomienia lub warunkowo wyświetlenia monitu, aby zamknąć okno dialogowe Program Visual Studio.  
  
## <a name="see-also"></a>Zobacz też  
 [Instalowanie pakietów VSPackage przy użyciu Instalatora Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)