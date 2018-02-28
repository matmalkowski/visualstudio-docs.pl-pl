---
title: "Włączanie funkcji debugowania w programie Visual C++ (-D_DEBUG) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0f1067ee5b60b8a8a402c9612357f2d83b6da138
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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