---
title: Ciągi podstawienia używane w. Pkgdef i. Pliki Pkgundef | Dokumentacja firmy Microsoft
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
- Visual Studio shell, isolated mode%2C .pkgdef and .pkgundef files
ms.assetid: b1755d63-d794-4fd7-864b-70a9684881c2
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 24996e4e32ab86af46fce5280947719f906ffc3a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42681079"
---
# <a name="substitution-strings-used-in-pkgdef-and-pkgundef-files"></a>Ciągi podstawienia używane w. Pkgdef i. Pliki Pkgundef
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [podstawienia ciągi używane w. Pkgdef i. Pliki Pkgundef](https://docs.microsoft.com/visualstudio/extensibility/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files).  
  
Można użyć ciągów podstawienia wymienione poniżej w pkgdef i pkgundef plików, należy zdefiniować dla programu Visual Studio isolated shell aplikacji.  
  
## <a name="substitution-strings"></a>Ciągi podstawienia  
  
|String|Opis|  
|------------|-----------------|  
|$=*RegistryEntry*$|Wartość *RegistryEntry* wpisu. Jeśli ciąg wpis rejestru kończy się znakiem ukośnika odwrotnego (\\), zostanie użyta domyślna wartość podklucza rejestru. Na przykład podstawienia ciągu $= HKEY_CURRENT_USER\Environment\TEMP$ jest rozwinięty folder tymczasowy bieżącego użytkownika.|  
|$AppName$|Kwalifikowana nazwa aplikacji, który jest przekazywany do AppEnv.dll punkty wejścia. Kwalifikowana nazwa składa się z nazwy aplikacji, podkreślenia i identyfikator klasy (CLSID) obiektu automatyzacji aplikacji, który jest zarejestrowany jako wartość ustawienia ThisVersionDTECLSID w pliku .pkgdef projektu.|  
|$AppDataLocalFolder|Podfolderu w folderze % LOCALAPPDATA % dla tej aplikacji.|  
|$BaseInstallDir$|Pełna ścieżka lokalizacji, w którym zainstalowano program Visual Studio.|  
|$CommonFiles$|Wartość zmiennej środowiskowej % CommonProgramFiles %.|  
|$MyDocuments$|Pełna ścieżka folderu Moje dokumenty bieżącego użytkownika.|  
|$PackageFolder$|Pełna ścieżka katalogu, który zawiera pliki zestawu pakietu dla aplikacji.|  
|$ProgramFiles$|Wartość zmienna środowiskowa % ProgramFiles %.|  
|$RootFolder$|Pełna ścieżka katalogu głównego aplikacji.|  
|$RootKey$|Główny klucz rejestru dla aplikacji. Domyślnie katalog główny jest w HKEY_CURRENT_USER\Software\\*CompanyName*\\*ProjectName*\\*Numerwersji* (gdy Aplikacja jest uruchomiona, _Config jest dołączany do tego klucza). Jest on ustawiony przez wartość RegistryRoot *SolutionName*plik .pkgdef.<br /><br /> Ciąg $ $RootKey może służyć do pobierania wartości rejestru w podkluczu aplikacji. Na przykład ciąg "$= $RootKey \AppIcon$" zwróci wartość AppIcon wpis w podkluczu katalogu głównego aplikacji.<br /><br /> Analizator przetwarza sekwencyjnie plik .pkgdef i będą mogli wpisu rejestru w podkluczu aplikacji tylko wtedy, gdy wpis został wcześniej zdefiniowany|  
|$ShellFolder$|Pełna ścieżka lokalizacji, w którym zainstalowano program Visual Studio.|  
|$System$|Do folderu Windows\system32.|  
|$WINDIR$|Windows folder.|  
  
 Jeżeli Analizator nie rozpoznaje ciąg podstawienia nie może ustalić wartości wpisu rejestru lub zmienną środowiskową, a następnie podstawienia nie są wykonywane w tej części ciągu.

