---
title: VSG_DEFAULT_RUN_FILENAME | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea549d2f-c857-458c-93c7-bc5a2d11d15d
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d82052c48444c8c22f205326cfb5ce614ac36aa7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42629813"
---
# <a name="vsgdefaultrunfilename"></a>VSG_DEFAULT_RUN_FILENAME
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [VSG_DEFAULT_RUN_FILENAME](https://docs.microsoft.com/visualstudio/debugger/graphics/vsg-default-run-filename).  
  
Definiuje domyślną nazwę pliku pliku dziennika grafiki.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
#define VSG_DEFAULT_FILENAME filename  
```  
  
#### <a name="parameters"></a>Parametry  
 `filename`  
 Nazwa pliku nadaną domyślnie plik dziennika grafiki podczas przechwytywania informacji graficznych programowo.  
  
## <a name="value"></a>Wartość  
 Plik dziennika ciąg literału, który reprezentuje nazwę pliku w oknie grafiki. Domyślnie L"default.vsglog".  
  
```cpp  
#define VSG_DEFAULT_FILENAME L"default.vsglog"  
```  
  
## <a name="remarks"></a>Uwagi  
 Jeśli symbol preprocesora `DONT_SAVE_VSGLOG_TO_TEMP` jest zdefiniowany, następnie nazwa pliku jest określana względem bieżącego katalogu przechwyconych aplikacji lub jest ścieżką bezwzględną; w przeciwnym razie jest określana względem katalogu plików tymczasowych użytkownika i nie może być ścieżką bezwzględną.  
  
 Aby zmienić nazwę pliku zdefiniowane, trzeba będzie ponownie zdefiniować je przed wprowadzeniem `vsgcapture.h` w programach.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano sposób zmiany pliku przechwytywania domyślnej nazwy pliku:  
  
```cpp  
// Redefine the default capture filename before including vsgcapture.h  
#define VSG_DEFAULT_FILENAME L"capture.vsglog"  
  
#include <vsgcapture.h>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [DONT_SAVE_VSGLOG_TO_TEMP](../debugger/dont-save-vsglog-to-temp.md)



