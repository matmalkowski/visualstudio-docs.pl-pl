---
redirect_url: shell/isolated-shell-entry-point-parameters-cpp
title: "Izolowane parametrów punktów wejścia powłoki (C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Shell [Visual Studio], isolated mode, Start entry point
- Visual Studio shell, isolated mode, Start entry point
ms.assetid: 18f4b18b-2173-4afa-ba0a-42fe33e61118
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b145207a2c74d47208df391c319f496467ae6438
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="isolated-shell-entry-point-parameters-c"></a>Parametry punktu wejścia programu Isolated Shell (C++)
Po uruchomieniu aplikacją programu Visual Studio shell wywołuje początkowy punkt wejścia programu Visual Studio shell. Następujące ustawienia można zastąpić w wywołaniu początkowy punkt wejścia powłoki. Aby uzyskać opis każdego ustawienia, zobacz [. Pliki Pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md).  
  
-   AddinsAllowed  
  
-   AllowsDroppedFilesOnMainWindow  
  
-   Nazwa aplikacji  
  
-   CommandLineLogo  
  
-   DefaultHomePage  
  
-   DefaultProjectsLocation  
  
-   DefaultSearchPage  
  
-   DefaultUserFilesFolderRoot  
  
-   DisableOutputWindow  
  
-   HideMiscellaneousFilesByDefault  
  
-   HideSolutionConcept  
  
-   NewProjDlgInstalledTemplatesHdr  
  
-   NewProjDlgSlnTreeNodeTitle  
  
-   SolutionFileCreatorIdentifier  
  
-   SolutionFileExt  
  
-   UserFilesSubFolderName  
  
-   UserOptsFileExt  
  
 Visual Studio Shell izolowanego szablon tworzy plik źródłowy *Nazwa rozwiązania*.cpp, gdzie *Nazwa rozwiązania* jest nazwa rozwiązania dla aplikacji. Ten plik definiuje główny punkt wejścia dla aplikacji, funkcję _tWinMain. Ta funkcja wywołuje punkt wejścia uruchamiania powłoki.  
  
 Zmiana tych ustawień podczas uruchamiania aplikacji można zmienić zachowanie aplikacji.  
  
## <a name="parameters"></a>Parametry  
 Początkowy punkt wejścia programu Visual Studio shell definiuje pięć parametrów. Nie należy zmieniać pierwsze cztery parametry. Parametrowi piątej przyjmuje listę zastąpienie ustawień. Punkt wejścia uruchamiania powłoki jest wywoływana z główny punkt wejścia aplikacji.  
  
 Punkt wejścia uruchamiania powłoki ma następującą sygnaturą.  
  
```  
typedef int (__cdecl *STARTFCN)(LPSTR, LPWSTR, int, GUID *, WCHAR *pszSettings);  
```  
  
 Jeśli nie chcesz zastąpić wszystkie ustawienia aplikacji, pozostaw wartość ustawienia zastępowania parametru jako wskaźnika o wartości null.  
  
 Aby zastąpić jedno lub więcej ustawień, przekazać ciąg Unicode, który zawiera ustawienia, które mają zostać zastąpiona. Ten ciąg jest rozdzielana średnikami lista par nazwa wartość. Każda para zawiera nazwę ustawienia, aby zastąpić, następuje znak równości (=), a następnie wartość, aby zastosować ustawienia.  
  
> [!NOTE]
>  Nie dołączaj odstępu w ciągów Unicode.  
  
 Dla ustawienia logiczna następujące ciągi reprezentuje wartość true; wszystkie inne ciągi reprezentuje wartość false. Te ciągi jest rozróżniana wielkość liter.  
  
-   \+  
  
-   1  
  
-   -1  
  
-   on  
  
-   true  
  
-   Tak  
  
## <a name="example"></a>Przykład  
 Aby wyłączyć dodatki i zmiany domyślnej lokalizacji projektów aplikacji, można ustawić ostatniego parametru do "AddinsAllowed=false;DefaultProjectsLocation=%USERPROFILE%\temp".  
  
## <a name="see-also"></a>Zobacz też  
 [Dostosowywanie programu Isolated Shell](../extensibility/customizing-the-isolated-shell.md)   
 [. Plików Pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)