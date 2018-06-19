---
title: Devenv.exe ustawienia przełącznika
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- setup Devenv switch
- /setup Devenv switch
- Devenv, /setup switch
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 0f3d78ebb63434df38735bdf24e9d4fcba8f172c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31942955"
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

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)