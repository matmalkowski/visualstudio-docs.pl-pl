---
title: Narzędzie CreatePkgDef | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0809c7acde2959fb91aa964fec137f63a7a995dc
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500699"
---
# <a name="createpkgdef-utility"></a>Narzędzie CreatePkgDef
Pobiera plik .dll dla rozszerzenia programu Visual Studio, jako parametr i tworzy *.pkgdef* pliku, który towarzyszy *.dll* pliku. *.Pkgdef* plik zawiera wszystkie informacje, które w przeciwnym razie powinny być zapisane w rejestrze systemu, gdy rozszerzenie jest zainstalowane.  
  
> [!NOTE]
>  Większość szablonów projektu, które są objęte zestawu SDK programu Visual Studio automatycznie utworzyć *.pkgdef* pliki jako część procesu kompilacji. Ten dokument jest przeznaczony dla osób, które chcesz ręcznie tworzyć pakiety lub konwertowania istniejących pakietów do użycia *.pkgdef* wdrożenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
CreatePkgDef /out=<FileName> [/codebase] [/assembly] <AssemblyPath>  
```  
  
## <a name="arguments"></a>Argumenty  
 **/ out =&lt;nazwy pliku&gt;**  
 Wymagane. Ustawia nazwę *.pkgdef* plik wyjściowy będzie &lt;FileName&gt;.  
  
 **/ codebase**  
 Opcjonalna. Wymusza rejestrację przy użyciu **CodeBase** narzędzia.  
  
 **/ Assembly**  
 Wymusza rejestrację przy użyciu **zestawu** narzędzia.  
  
 **&lt;Ścieżkazestawu&gt;**  
 Ścieżka *.dll* pliku, z którego chcesz wygenerować *.pkgdef*.  
  
## <a name="remarks"></a>Uwagi  
 Rozwój rozszerzeń przy użyciu *.pkgdef* plików zastępuje wymagania rejestru wcześniejszych wersji programu Visual Studio.  
  
 *.Pkgdef* pliki muszą być zainstalowane w jednym z następujących lokalizacji: 

 - *%localappdata%\Microsoft\Visual Studio\14.0\Extensions\\* 
 
 - *%vsinstalldir%\Common7\IDE\Extensions\\*
    
 Jeśli folder instalacji to *%localappdata%\Microsoft\Visual Studio\14.0\Extensions\\*, rozszerzenie zostanie rozpoznane przez program Visual Studio, ale zostanie domyślnie wyłączona. Użytkownik może włączyć rozszerzenie za pomocą **rozszerzenia i aktualizacje**. 
   
 Jeśli folder instalacji to *%vsinstalldir%\Common7\IDE\Extensions\\*, rozszerzenie jest domyślnie włączona.  
  
> [!NOTE]
>  **Rozszerzenia i aktualizacje** narzędzie nie może służyć do dostępu do rozszerzenia, chyba, że jest zainstalowany jako część pakietu VSIX.  
  
## <a name="see-also"></a>Zobacz także  
 [Narzędzie CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md)