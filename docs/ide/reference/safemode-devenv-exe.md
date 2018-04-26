---
title: -Tryb awaryjny (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: eaf137b699b7a02a0ee79099e937767262fce4e9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)
Uruchamia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] w trybie awaryjnym, ładowanie tylko domyślnego środowiska i usług.

## <a name="syntax"></a>Składnia

```
devenv /SafeMode
```

## <a name="remarks"></a>Uwagi
 Ten przełącznik zapobiega podczas ładowania wszystkich innych firm VSPackages [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zostanie uruchomiony, w związku z tym zapewnienia stabilnej wykonywania.

## <a name="description"></a>Opis
 W następującym przykładzie uruchomiono [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] w trybie awaryjnym.

## <a name="code"></a>Kod

```
Devenv.exe /SafeMode
```

## <a name="see-also"></a>Zobacz też

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)