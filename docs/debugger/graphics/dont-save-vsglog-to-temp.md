---
title: DONT_SAVE_VSGLOG_TO_TEMP | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: f27ab0e6-9575-4ca0-9901-37d3e5c3a2f5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b70ddf2933b8bd2d96db1636612cb35a6a759a1a
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31473809"
---
# <a name="dontsavevsglogtotemp"></a>DONT_SAVE_VSGLOG_TO_TEMP
Definiuje jego obecność czy grafiki pliku dziennika są zapisywane w katalogu plików tymczasowych użytkownika.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
#define DONT_SAVE_VSGLOG_TO_TEMP  
```  
  
## <a name="value"></a>Wartość  
 Symbol preprocesora, który określa, czy plik dziennika grafiki na podstawie obecności lub braku jest zapisywany w katalogu plików tymczasowych użytkownika. Jeśli ten symbol jest zdefiniowana, a następnie nazwę pliku zdefiniowane przez `VSG_DEFAULT_RUN_FILENAME` jest powiązane z bieżącym katalogiem przechwyconych aplikacji lub jest ścieżką bezwzględną; w przeciwnym razie nazwa pliku zdefiniowana przez `VSG_DEFAULT_RUN_FILENAME` jest określana względem katalogu plików tymczasowych użytkownika i nie może być Ścieżka bezwzględna.  
  
## <a name="remarks"></a>Uwagi  
 W zależności od uprawnień użytkownika plik dziennika grafiki nie może być można zapisać w dowolnej lokalizacji. Zaleca się, że wolisz zapisać dzienniki grafiki w katalogu plików tymczasowych użytkownika lub innego znanego dobrego lokalizacji, jeśli nie wiesz, czy należy wybrać lokalizację mogą być zapisywane na przez użytkownika.  
  
 Aby zapobiec grafiki pliku dziennika są zapisywane w katalogu plików tymczasowych, muszą zdefiniowane `DONT_SAVE_VSGLOG_TO_TEMP` przed wprowadzeniem `vsgcapture.h`.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano, jak można zapisać pliku dziennika grafiki ścieżką bezwzględną na komputerze hosta.  
  
```  
// Define DONT_SAVE_VSGLOG_TO_TEMP and VSG_DEFAULT_RUN_FILENAME before including vsgcapture.h  
#define DONT_SAVE_VSGLOG_TO_TEMP  
#define VSG_DEFAULT_RUN_FILENAME L"C:\\Graphics Diagnostics Captures\\default.vsglog"  
  
#include <vsgcapture.h>  
  
```  
  
## <a name="see-also"></a>Zobacz też  
 [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)