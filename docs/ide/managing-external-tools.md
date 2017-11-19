---
title: "Zarządzanie narzędziami zewnętrznymi | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/17/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.externaltools
helpviewer_keywords:
- Create GUID tool
- RC (Resource Compiler)
- ReBase tool
- Windows NT Message Compiler
- Windows NT C++ Symbol Undecorator
- tstcon32.exe
- Type Library Generator
- Windows NT Image Binder
- tools [Visual Studio], external
- RowsetViewer tool
- utilities, external tools
- Local Test Manager
- OLE DB Rowset Viewer
- Midlc (IDL Compiler)
- ATL Trace Tool
- Odbcte32w.exe
- IDL Compiler
- HCW (Help Workshop)
- Message Compiler [Visual Studio]
- UUID Generator
- MIDL, external tools
- ErrLook tool
- MAKEHM tool
- Error lookup tool
- OLEVIEW (Object Viewer)
- Uuidgen.exe
- WebDbg tool
- OLE/COM Object Viewer
- LTM (Local Test Manager)
- ATLTraceTool.exe
- Bind tool
- Vsvars32.bat
- external tools [Visual Studio]
- ODBC Test
- Windows NT Image Rebaser
- undname.exe
- Vcspawn.exe
- ActiveX Control Test Container
- mc (Message Compiler)
- GUIDGEN tool
- Odbcte32.exe
- DisableMsg tool
- MkTypLib tool
- Help Workshop
- Resource Compiler
ms.assetid: f382fd40-a98f-4934-8c9a-5aeae881acde
caps.latest.revision: "38"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9829887a28ec2e672999732e38604f3d9d6fea9a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="manage-external-tools"></a>Zarządzanie narzędziami zewnętrznymi
Można wywołać narzędzia zewnętrznego w programie Visual Studio za pomocą **narzędzia** menu. Kilka domyślne narzędzia są dostępne z **narzędzia** menu, ale można dodać inne pliki wykonywalne własny.  

## <a name="tools-available-on-the-visual-studio-tools-menu"></a>Narzędzia dostępne w menu programu Visual Studio Tools
 **Narzędzia** menu zawiera kilka wbudowanych poleceń, takich jak:

*  **Rozszerzenia i aktualizacje** dla [Zarządzanie rozszerzenia programu Visual Studio](finding-and-using-visual-studio-extensions.md)
*  **Menedżer wstawek kodu...**  dla [organizowanie wstawki kodu](code-snippets.md#code-snippet-manager)
*  **Ochrona cenią sobie wcześniejsze — Dotfuscator** uruchomienie [Dotfuscator Community Edition (CE)](dotfuscator/index.md) Jeśli jest [zainstalowany](dotfuscator/install.md)
*  **Dostosuj...**  dla [Dostosowywanie menu i pasków narzędzi](how-to-customize-menus-and-toolbars-in-visual-studio.md)
*  **Opcje...**  dla [ustawienie szereg różnych opcji dla programu Visual Studio IDE i inne narzędzia](reference/options-dialog-box-visual-studio.md)

## <a name="add-new-tools-to-the-tools-menu"></a>Dodawanie nowych narzędzi do menu Narzędzia 
 Można dodać do zewnętrznego narzędzia **narzędzia** menu. Otwórz **zewnętrznych narzędzi...**  okno dialogowe i kliknij przycisk **Dodaj**, a następnie wypełnij informacje. Na przykład następujący wpis powoduje Eksploratora Windows, aby otworzyć znajduje się w katalogu pliku, który aktualnie otwarte w programie Visual Studio:  
  
1.  Nazwa: *Otwórz lokalizację pliku*
  
2.  Polecenie:`explorer.exe`  
  
3.  Argumenty:`/root, "$(ItemDir)"`  
  
 Poniżej znajduje się pełna lista argumentów, które mogą być używane podczas definiowania narzędzia zewnętrznego.
  
> [!NOTE]
>  Pasek stanu IDE przedstawia zmienne bieżącego wiersza i bieżącej kolumny, aby wskazać, gdy punkt wstawiania znajduje się w edytorze kodu active. Zmienna tekst zwraca tekst lub wybrane w tej lokalizacji kodu.  
  
|Nazwa|Argument|Opis|  
|----------|--------------|-----------------|  
|Ścieżka elementu|$(ItemPath)|Pełnej nazwy pliku bieżącego pliku (dysk + ścieżka pliku nazwy).|  
|Element katalogu|$(ItemDir)|Katalog bieżącego pliku (dysk + ścieżki).|  
|Nazwa pliku elementu|$(ItemFilename)|Nazwa pliku bieżącego pliku (nazwa pliku).|  
|Rozszerzenia elementu|$(ItemExt)|Rozszerzenie nazwy pliku bieżącego pliku.|  
|Bieżący wiersz|$(CurLine)|Bieżącej pozycji kursora w oknie kodu.|  
|Bieżącej kolumny|$(CurCol)|Bieżąca kolumna pozycja kursora w oknie kodu.|  
|Tekst|$(CurText)|Zaznaczonego tekstu.|  
|Ścieżka docelowa|$(Targetpath) —|Pełnej nazwy pliku elementu, który ma zostać utworzony (dysk + ścieżka pliku nazwy).|  
|Katalog docelowy|$(Targetdir) —|Katalog elementu, który ma zostać utworzony.|  
|Nazwa obiektu docelowego|$(TargetName)|Nazwa pliku elementu, który ma zostać utworzony.|  
|Rozszerzenie docelowego|$(TargetExt)|Rozszerzenie nazwy pliku elementu, który ma zostać utworzony.|  
|Katalog danych binarnych|$(BinDir)|Lokalizacji końcowej pliku binarnego budowanego (zdefiniowany jako dysk + ścieżki). Na przykład:**\\... \My Studio \<wersji >\\< ProjectName\>\bin\debug**|  
|Katalog projektu|$(ProjDir)|Katalog bieżącego projektu (dysk + ścieżki).|  
|Nazwa pliku projektu|$(ProjFileName)|Nazwa pliku bieżącego projektu (dysk + ścieżka pliku nazwy).|  
|Katalog rozwiązań|$(SolutionDir)|Katalog bieżącego rozwiązania (dysk + ścieżki).|  
|Nazwa pliku rozwiązania|$(Solutionfilename) —|Nazwa pliku bieżącego rozwiązania (dysk + ścieżka pliku nazwy).|  

## <a name="see-also"></a>Zobacz także  
 [Narzędzia kompilacji C/C++](/cpp/build/reference/c-cpp-build-tools)
