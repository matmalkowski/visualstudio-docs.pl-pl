---
title: Odwołanie (przechwycenie programowe) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
ms.assetid: ef60eb8d-1ac2-4e3a-9b4b-f6da0bdd9da8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cf5a475c32fa1e9ecb3d376f7844ddbeeee7748c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="reference-programmatic-capture"></a>Odwołanie (przechwycenie programowe)
Diagnostyka grafiki obsługuje programowe kontrolę nad jego funkcji przechwytywania, za pośrednictwem programowe Przechwytywanie interfejsu API. Ten interfejs API umożliwia Przełącz i dodawać komunikaty do diagnostyki grafiki HUD (wyświetlanie Head w górę), zainicjować i utworzyć pliki dziennika grafiki i przechwytywanie informacji graficznych.  
  
## <a name="programmatic-capture-apis"></a>Interfejsy API przechwycenie programowe  
  
### <a name="classes"></a>Klasy  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[VsgDbg, klasa](vsgdbg-class.md)|Reprezentuje interfejs, za pomocą którego składników w aplikacji diagnostyki grafiki jest kontrolowany programowo.|  
  
### <a name="preprocessor-symbols"></a>Definicji symboli preprocesora  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)|Definiuje jego obecność czy grafiki pliku dziennika są zapisywane w katalogu plików tymczasowych użytkownika.|  
|[VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)|Definiuje domyślną nazwę pliku dla pliku dziennika grafiki.|  
|[VSG_NODEFAULT_INSTANCE](vsg-nodefault-instance.md)|Definiuje przez jego obecność czy domyślnego wystąpienia programu `VsgDbg` podano klasy.|  
  
## <a name="related-articles"></a>Powiązane artykuły  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Przechwytywanie informacji graficznych](capturing-graphics-information.md)|Pokazuje, jak przechwytywanie informacji graficznych z aplikacji opartych na technologii DirectX, aby mogli używać [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] narzędziami diagnostyki grafiki do diagnozowania problemów renderowania.|  
|[Omówienie](overview-of-visual-studio-graphics-diagnostics.md)|Pokazuje, jak diagnostyki grafiki można Debugowanie błędów renderowania w DirectX gier i aplikacji.|