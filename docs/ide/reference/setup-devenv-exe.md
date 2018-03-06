---
title: "Devenv.exe ustawienia przełącznika | Dokumentacja firmy Microsoft"
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- setup Devenv switch
- /setup Devenv switch
- Devenv, /setup switch
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e37fe50eefc36e7b5396f396d2b614851a0bd9cb
ms.sourcegitcommit: 873c0e1a31def013bcca1b0caa0eb0249de89bec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2018
---
# <a name="setup-devenvexe"></a>/Setup (devenv.exe)

/ Setup przełącznika przyczyny Visual Studio, aby scalić metadanych zasobów, które opisują menu, paski narzędzi i polecenia grup, wszystkie dostępne VSPackages.

## <a name="syntax"></a>Składnia

```shell
devenv /setup
```

## <a name="remarks"></a>Uwagi

Ten przełącznik nie przyjmuje żadnych argumentów. `devenv /setup` Polecenia jest zazwyczaj podawana jako ostatni etap procesu instalacji. Użycie `/setup` przełącznika nie Uruchom program Visual Studio.

> [!NOTE]
> Należy uruchomić `devenv` jako administrator, aby można było używać `/setup` przełącznika.

## <a name="example"></a>Przykład

Ten przykład przedstawia ostatni krok w instalacji wersji programu Visual Studio, który zawiera pakiety VSPackage.

```shell
devenv /setup
```

## <a name="see-also"></a>Zobacz także

[Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)