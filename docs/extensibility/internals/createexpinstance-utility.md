---
title: Narzędzie CreateExpInstance | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- experimental hive
- experimental instance
- createexpinstance
- createexpinst
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bdcb37374c63b96e2169de28c6fe21742024ca98
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128094"
---
# <a name="createexpinstance-utility"></a>Narzędzie CreateExpInstance
Narzędzia CreateExpInstance do tworzenia, zresetować, lub usuń eksperymentalne wystąpienie programu Visual Studio. Eksperymentalne wystąpienie służy do debugowania i testowania rozszerzeń programu Visual Studio bez zmiany podstawowego produktu.  
  
## <a name="syntax"></a>Składnia  
  
```  
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix  
```  
  
#### <a name="parameters"></a>Parametry  
 / Utwórz  
 Tworzy wystąpienie eksperymentalne.  
  
 / Reset  
 Usuwa wystąpienie eksperymentalne, a następnie tworzy nowy.  
  
 /Clean  
 Usuwa wystąpienie eksperymentalne.  
  
 / VSInstance  
 Nazwa katalogu, który zawiera wystąpienie programu Visual Studio podstawowej, aby skopiować.  
  
 / RootSuffix  
 Sufiks, który można dołączyć do nazwy katalogu eksperymentalne wystąpienie.  
  
## <a name="remarks"></a>Uwagi  
 Podczas pracy na rozszerzenia programu Visual Studio naciśnij klawisz F5, aby otworzyć eksperymentalne wystąpienie domyślne i zainstaluj bieżący rozszerzenie. Jeśli żadne wystąpienie eksperymentalne jest dostępny, program Visual Studio tworzy, który zawiera ustawienia domyślne.  
  
 Domyślna lokalizacja eksperymentalne wystąpienie zależy od numer wersji Visual Studio. Na przykład dla programu Visual Studio 2015, lokalizacja jest %localappdata%\Microsoft\VisualStudio\14.0Exp\ wszystkie pliki w lokalizacji katalogu są traktowane jako część tego wystąpienia. Wszelkie dodatkowe wystąpienia eksperymentalne nie zostanie załadowany przez program Visual Studio, chyba że zostanie zmieniona nazwa katalogu, do domyślnej lokalizacji.  
  
 Visual Studio nie dostępu do rejestru systemowego po jego otwarciu w eksperymentalnym wystąpieniu. Różni się to z wcześniejszych wersji programu Visual Studio, która używana wersja eksperymentalna gałęzi rejestru.  
  
 Narzędzie CreateExpInstance zastępuje narzędzie VsRegEx.  
  
 Poniższy przykład Resetuje domyślne eksperymentalne wystąpienie programu Visual Studio.  
  
 **CreateExpInstance.exe/reset / vsinstance = 14.0/rootsuffix = Exp**  
  
## <a name="see-also"></a>Zobacz też  
 [Pakiety VSPackage](../../extensibility/internals/vspackages.md)