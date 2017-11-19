---
title: "Rejestrowanie zleceń dla rozszerzeń nazw plików | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: verbs, registering
ms.assetid: 81a58e40-7cd0-4ef4-a475-c4e1e84d6e06
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8f430486c613e6281404110d4441d2a3d2100534
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="registering-verbs-for-file-name-extensions"></a>Rejestrowanie zleceń dla rozszerzeń nazw plików
Skojarzenie rozszerzenia nazwy pliku z aplikacją ma zazwyczaj preferowane działanie, gdy użytkownik kliknie dwukrotnie plik. To preferowane akcji jest połączony z zlecenie, na przykład po otwarciu umożliwiająca akcji.  
  
 Możesz zarejestrować zlecenia, które są skojarzone z identyfikator programowy (ProgID) dla rozszerzenia przy użyciu klawisza powłoki, znajduje się w wpisów z HKEY_CLASSES_ROOT\\*progid*\shell. Aby uzyskać więcej informacji, zobacz [typów plików](http://msdn.microsoft.com/library/windows/desktop/cc144148\(v=vs.85\).aspx).  
  
## <a name="registering-standard-verbs"></a>Rejestrowanie zleceń standardowych  
 System operacyjny rozpoznaje następujących zleceń standardowych:  
  
-   Otwarcie  
  
-   Edytowanie  
  
-   Play  
  
-   Drukuj  
  
-   Wersja zapoznawcza  
  
 Jeśli to możliwe, należy zarejestrować standardowe zlecenia. Wybór najczęściej używane jest zlecenie Otwórz. Zlecenie edycji należy używać tylko wtedy, gdy istnieje wyczyść różnica między otwierania pliku i edytowania pliku. Na przykład otwarcie pliku .htm wyświetla go w przeglądarce, natomiast edycji pliku .htm uruchamia edytora HTML. Standardowe są zlokalizowane z ustawień regionalnych systemu operacyjnego.  
  
> [!NOTE]
>  Podczas rejestrowania zleceń standardowych, nie należy ustawiać wartość domyślna otworzyć klucza. Wartość domyślna zawiera ciąg wyświetlany w menu. System operacyjny udostępnia tego ciągu dla zleceń standardowych.  
  
 Pliki projektu powinien być zarejestrowany w uruchomić nowe wystąpienie klasy [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] po otwarciu pliku. Poniższy przykład przedstawia rejestracji standardowe zlecenie [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projektu.  
  
```  
[HKEY_CLASSES_ROOT\.csproj]  
@="VisualStudio.csproj.8.0"  
  
[HKEY_CLASSES_ROOT\.csproj\OpenWithList]  
[HKEY_CLASSES_ROOT\.csproj\OpenWithList\VSLauncher.exe]  
@=""  
  
[HKEY_CLASSES_ROOT\.csproj\OpenWithProgids]  
"VisualStudio.csproj.8.0"=""  
  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe]  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell]  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open]  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open\Command]  
@="C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe \"%1\""  
  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0]  
@="C# Project file"  
  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\DefaultIcon]  
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,0"  
  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell]  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open]  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open\Command]  
@="\"C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe\" \"%1\""  
```  
  
 Aby otworzyć plik w istniejącym wystąpieniem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], zarejestruj klucz DDEEXEC. Poniższy przykład przedstawia rejestracji standardowe zlecenie [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] plik CS.  
  
```  
[HKEY_CLASSES_ROOT\.cs]  
@="VisualStudio.cs.8.0"  
  
[HKEY_CLASSES_ROOT\.cs\OpenWithList]  
[HKEY_CLASSES_ROOT\.cs\OpenWithList\devenv.exe]  
@=""  
  
[HKEY_CLASSES_ROOT\.cs\OpenWithProgids]  
"VisualStudio.cs.8.0"=""  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0]  
@="C# Source file"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\DefaultIcon]  
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,1"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell]  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open]  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\Command]  
@="\"C:\\VisualStudioPath\\Common7\\IDE\\devenv.exe\" /dde \"%1\""  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec]  
@="Open(\"%1\")"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Application]  
@="VisualStudio.8.0"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Topic]  
@="system"  
```  
  
## <a name="setting-the-default-verb"></a>Ustawienie domyślne zlecenie  
 Zlecenie domyślny jest akcja, która jest wykonywana, gdy użytkownik kliknie dwukrotnie plik w Eksploratorze Windows. Zlecenie domyślny jest określone jako wartość domyślną dla wpisów z HKEY_CLASSES_ROOT zlecenie\\*progid*\Shell klucza. Jeśli nie określono wartości, zlecenie domyślny jest określone w HKEY_CLASSES_ROOT zlecenie pierwszy\\*progid*\Shell listę kluczy.  
  
> [!NOTE]
>  Jeśli zamierzasz zmienić domyślne zlecenie dla rozszerzenia we wdrożeniu side-by-side, należy wziąć pod uwagę wpływ na instalację i usuwanie. Podczas instalacji zostanie zastąpiony oryginalnej wartości domyślnej.  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie skojarzeń plików Side-by-Side](../extensibility/managing-side-by-side-file-associations.md)