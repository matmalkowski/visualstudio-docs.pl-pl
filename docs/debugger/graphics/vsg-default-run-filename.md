---
title: VSG_DEFAULT_RUN_FILENAME | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea549d2f-c857-458c-93c7-bc5a2d11d15d
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3604842dd2d84af4598b65c83cc2999930b89edf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="vsgdefaultrunfilename"></a>VSG_DEFAULT_RUN_FILENAME
Definiuje domyślną nazwę pliku dla pliku dziennika grafiki.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
#define VSG_DEFAULT_FILENAME filename  
```  
  
#### <a name="parameters"></a>Parametry  
 `filename`  
 Nazwa pliku nadawane domyślnie plik dziennika grafiki podczas przechwytywania informacji graficznych programowo.  
  
## <a name="value"></a>Wartość  
 Ciąg literału, która reprezentuje nazwę pliku grafiki pliku dziennika. Domyślnie L"default.vsglog".  
  
```C++  
#define VSG_DEFAULT_FILENAME L"default.vsglog"  
```  
  
## <a name="remarks"></a>Uwagi  
 Jeśli symbol preprocesora `DONT_SAVE_VSGLOG_TO_TEMP` jest zdefiniowany, następnie nazwa pliku jest powiązane z bieżącym katalogiem przechwyconych aplikacji lub jest ścieżką bezwzględną; w przeciwnym razie jest określana względem katalogu plików tymczasowych użytkownika i nie może być ścieżką bezwzględną.  
  
 Aby zmienić nazwę pliku zdefiniowane, trzeba będzie ponownie zdefiniować jego przed wprowadzeniem `vsgcapture.h` w programie.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano, jak zmienić plik przechwytywania domyślna nazwa pliku:  
  
```C++  
// Redefine the default capture filename before including vsgcapture.h  
#define VSG_DEFAULT_FILENAME L"capture.vsglog"  
  
#include <vsgcapture.h>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)