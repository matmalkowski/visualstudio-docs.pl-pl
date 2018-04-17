---
title: Devenv.exe ustawienia przełącznika | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- setup Devenv switch
- /setup Devenv switch
- Devenv, /setup switch
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: eee6e30a7489f5097cb17a19513c2a423187c827
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
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