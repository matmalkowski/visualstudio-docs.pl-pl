---
redirect_url: shell/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files
title: "Używane w ciągi podstawienia. Pkgdef i. Pliki Pkgundef | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode, .pkgdef and .pkgundef files
ms.assetid: b1755d63-d794-4fd7-864b-70a9684881c2
caps.latest.revision: "4"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 220e6d9bb9d360a51f9a83b5d0b4420cf64aef91
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="substitution-strings-used-in-pkgdef-and-pkgundef-files"></a>Używane w ciągi podstawienia. Pkgdef i. Pliki Pkgundef
Można użyć ciągów podstawienia wymienione poniżej w .pkgdef i pliki .pkgundef zdefiniowane dla Visual Studio izolowany aplikacji powłoki.  
  
## <a name="substitution-strings"></a>Ciągi podstawienia  
  
|String|Opis|  
|------------|-----------------|  
|$=*RegistryEntry*$|Wartość *RegistryEntry* wpisu. Jeśli ciąg wpisu rejestru kończy się ukośnikiem (\\), a następnie zostanie użyta domyślna wartość podklucza rejestru. Na przykład podstawienie ciągu $= HKEY_CURRENT_USER\Environment\TEMP$ jest rozwinięty do tymczasowego folderu bieżącego użytkownika.|  
|$AppName$|Kwalifikowana nazwa aplikacji, która została przekazana do AppEnv.dll punktów wejścia. Nazwa kwalifikowana składa się z nazwy aplikacji, podkreślenia i identyfikator klasy (CLSID) obiektu automatyzacji aplikacji, który jest zarejestrowany jako wartość ustawienia ThisVersionDTECLSID w pliku .pkgdef projektu.|  
|$AppDataLocalFolder|Podfolderze LOCALAPPDATA % dla tej aplikacji.|  
|$BaseInstallDir$|Pełna ścieżka lokalizacji, w którym został zainstalowany program Visual Studio.|  
|$CommonFiles$|Wartość zmiennej środowiskowej % CommonProgramFiles %.|  
|$MyDocuments$|Pełna ścieżka folderu Moje dokumenty bieżącego użytkownika.|  
|$PackageFolder$|Pełna ścieżka katalogu, który zawiera pliki zestawu pakietu dla aplikacji.|  
|$ProgramFiles$|Wartość zmiennej środowiskowej % ProgramFiles %.|  
|$RootFolder$|Pełna ścieżka katalogu głównego aplikacji.|  
|$RootKey$|Klucz główny rejestru dla aplikacji. Domyślnie główny jest w HKEY_CURRENT_USER\Software\\*NazwaFirmy*\\*ProjectName*\\*Numerwersji* (gdy Aplikacja jest uruchomiona, _Config zostaje dołączony do tego klucza). Jest on ustawiony przez wartość RegistryRoot *Nazwa rozwiązania*.pkgdef pliku.<br /><br /> Ciąg $ $RootKey może służyć do pobierania wartości rejestru w podkluczu aplikacji. Na przykład ciąg "$= $RootKey$ \AppIcon$" zwróci wartość wpisu AppIcon podkluczu katalogu głównego aplikacji.<br /><br /> Analizator przetwarza plik .pkgdef sekwencyjnie i mogą uzyskiwać dostęp do wpisu rejestru podkluczu aplikacji tylko wtedy, gdy wpis został wcześniej zdefiniowany|  
|$ShellFolder$|Pełna ścieżka lokalizacji, w którym został zainstalowany program Visual Studio.|  
|$System$|Folderze Windows\system32.|  
|$WINDIR$|Folder systemu Windows.|  
  
 Jeżeli Analizator nie rozpoznaje ciąg podstawienia lub nie można określić wartości wpisu rejestru lub zmiennej środowiskowej, a następnie podstawienia nie są wykonywane w tej części ciągu.