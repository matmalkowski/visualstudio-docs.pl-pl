---
title: Lista modułów — polecenie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- debug.listmodules
helpviewer_keywords:
- Debug.ListModules command
- ListModules command
- list modules command
ms.assetid: 3cb73774-6ac0-43b2-b781-75ed47175bfd
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1593879f59642347f58d9c8229aac7d2a9d70261
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42680496"
---
# <a name="list-modules-command"></a>Lista modułów — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [lista modułów — polecenie](https://docs.microsoft.com/visualstudio/ide/reference/list-modules-command).  
  
  
Wyświetla listę modułów dla bieżącego procesu.  
  
## <a name="syntax"></a>Składnia  
  
```  
Debug.ListModules [/Address:yes|no] [/Name:yes|no] [/Order:yes|no]  
[/Path:yes|no] [/Process:yes|no] [/SymbolFile:yes|no]  
[/SymbolStatus:yes|no] [/Timestamp:yes|no] [/Version:yes|no]  
```  
  
#### <a name="parameters"></a>Parametry  
 / Adres:`yes|no`  
 Opcjonalna. Określa, czy ma być wyświetlana adresów pamięci modułów. Wartość domyślna to `yes`.  
  
 / Name:`yes|no`  
 Opcjonalna. Określa, czy pokazać nazwy modułów. Wartość domyślna to `yes`.  
  
 / Order:`yes|no`  
 Opcjonalna. Określa, czy z kolejnością modułów. Wartość domyślna to `no`.  
  
 / Path:`yes|no`  
 Opcjonalna. Określa, czy ma być wyświetlana ścieżki modułów. Wartość domyślna to `yes`.  
  
 / Process:`yes|no`  
 Opcjonalna. Określa, czy ma być wyświetlana procesy modułów. Wartość domyślna to `no`.  
  
 / SymbolFile:`yes|no`  
 Opcjonalna. Określa, czy ma być wyświetlana pliki symboli modułów. Wartość domyślna to `no`.  
  
 / SymbolStatus:`yes|no`  
 Opcjonalna. Określa, czy mają być wyświetlane stany symboli modułów. Wartość domyślna to `yes`.  
  
 / Sygnatura czasowa:`yes|no`  
 Opcjonalna. Określa, czy ma być wyświetlana sygnatury czasowe modułów. Wartość domyślna to `no`.  
  
 / Version:`yes|no`  
 Opcjonalna. Określa, czy ma być wyświetlana wersje modułów. Wartość domyślna to `no`.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="example"></a>Przykład  
 W tym przykładzie zawiera listę nazw modułów, adresów i sygnatury czasowe dla bieżącego procesu.  
  
```  
Debug.ListModules /Address:yes /Name:yes /Order:no /Path:no /Process:no /SymbolFile:no /SymbolStatus:no /Timestamp:yes /Version:no  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Porady: Korzystanie z okna modułów](../../debugger/how-to-use-the-modules-window.md)



