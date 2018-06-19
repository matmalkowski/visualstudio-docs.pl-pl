---
title: Włączanie funkcji debugowania w programie Visual C++ (-D_DEBUG) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- /D_DEBUG compiler option [C++]
- debugging [C++], enabling debug features
- debugging [MFC], enabling debug features
- assertions, enabling debug features
- D_DEBUG compiler option
- MFC libraries, debug version
- debug builds, MFC
- _DEBUG macro
ms.assetid: 276e2254-7274-435e-ba4d-67fcef4f33bc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 5298879d93bf4e86df7610d5891e73bdbb67c4a1
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31472581"
---
# <a name="enabling-debug-features-in-visual-c-ddebug"></a>Włączanie funkcji debugowania w programie Visual C++ (/D_DEBUG)
W [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], debugowanie funkcji, takich jak potwierdzenia są włączone podczas kompilowania programu symbolem **_DEBUG** zdefiniowane. Można zdefiniować **_DEBUG** w jeden z dwóch sposobów:  
  
-   Określ **#define _DEBUG** w kodzie źródłowym lub  
  
-   Określ **/D_DEBUG** — opcja kompilatora. (Jeśli tworzysz projekt w programie Visual Studio za pomocą kreatorów, **/D_DEBUG** jest automatycznie zdefiniowany w konfiguracji debugowania.)  
  
 Gdy **_DEBUG** jest zdefiniowany, kompilator kompiluje fragmentów kodu otoczona **#ifdef _DEBUG** i `#endif`.  
  
 Konfiguracja debugowania programu MFC musi łączyć się z wersji biblioteki MFC do debugowania. Pliki nagłówka MFC ustalić poprawnej wersji biblioteki MFC, aby połączyć z oparta na symbole zdefiniowane, takich jak **_DEBUG** i **_unicode —**. Aby uzyskać więcej informacji, zobacz [wersje biblioteki MFC](/cpp/mfc/mfc-library-versions).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)   
 [Ustawienia projektu dla konfiguracji debugowania z C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)