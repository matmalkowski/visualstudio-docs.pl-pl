---
title: "Narzędzie elementu CreatePkgDef | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 32e9c8ffa2a9ca2bba889436f37cc4f5c3d188bf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="createpkgdef-utility"></a>Narzędzie elementu CreatePkgDef
Plik DLL rozszerzenia programu Visual Studio jako parametr przyjmuje i tworzy plik .pkgdef towarzyszące biblioteki dll. Plik .pkgdef zawiera wszystkie informacje, które w przeciwnym razie będzie zapisany w rejestrze systemu, gdy rozszerzenie jest zainstalowane.  
  
> [!NOTE]
>  Większość szablonów projektu, które znajdują się w programie Visual Studio SDK automatycznie Utwórz pliki .pkgdef jako część procesu kompilacji. Ten dokument jest przeznaczony dla osób chcących tworzyć pakiety ręcznie lub przekonwertować istniejące pakiety przy użyciu .pkgdef wdrażania.  
  
## <a name="syntax"></a>Składnia  
  
```  
CreatePkgDef /out=FileName [/codebase] [/assembly] AssemblyPath  
```  
  
## <a name="arguments"></a>Argumenty  
 / out =`FileName`  
 Wymagany. Ustawia nazwę pliku wyjściowego .pkgdef do`FileName`.  
  
 /codebase  
 Opcjonalny. Wymusza rejestracja za pomocą narzędzia CodeBase.  
  
 / Assembly  
 Wymusza rejestrację przy użyciu narzędzia do zestawu.  
  
 `AssemblyPath`  
 Ścieżka pliku dll, z którego chcesz wygenerować .pkgdef.  
  
## <a name="remarks"></a>Uwagi  
 Rozszerzenie wdrożenia przy użyciu plików .pkgdef zamienia wymagania rejestru wcześniejszych wersji programu Visual Studio.  
  
 Pliki .pkgdef muszą być zainstalowane w jednym z następujących lokalizacji: %localappdata%\Microsoft\Visual Studio\14.0\Extensions\ lub %vsinstalldir%\Common7\IDE\Extensions\\. Jeśli folder instalacji to %localappdata%\Microsoft\Visual Studio\14.0\Extensions\\, rozszerzenie zostanie rozpoznany przez program Visual Studio, ale będzie domyślnie wyłączone. Użytkownika można włączyć rozszerzenia przy użyciu **rozszerzenia i aktualizacje**. Jeśli folder instalacji to %vsinstalldir%\Common7\IDE\Extensions\\, rozszerzenie jest domyślnie włączona.  
  
> [!NOTE]
>  **Rozszerzenia i aktualizacje** narzędzia nie można uzyskać dostępu do rozszerzenia, chyba że jest zainstalowana jako część pakietu VSIX.  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzie CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md)