---
title: "Devenv.exe ustawienia przełącznika | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- setup Devenv switch
- /setup Devenv switch
- Devenv, /setup switch
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 93f03de74540d130d66ce123b355691e0828b93e
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2018
---
# <a name="setup-devenvexe"></a>/Setup (devenv.exe)

/ Setup przełącznika przyczyny Visual Studio, aby scalić metadanych zasobów, które opisują menu, paski narzędzi i polecenia grup, wszystkie dostępne VSPackages.

## <a name="syntax"></a>Składnia

```
devenv /setup
```

## <a name="remarks"></a>Uwagi

Ten przełącznik nie przyjmuje żadnych argumentów. `devenv /setup` Polecenia jest zazwyczaj podawana jako ostatni etap procesu instalacji. Użycie `/setup` przełącznika nie Uruchom program Visual Studio.

Należy uruchomić `devenv` jako administrator, aby można było używać [/Setup (devenv.exe)](../../ide/reference/setup-devenv-exe.md) i [/installvstemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md) przełączników.

## <a name="example"></a>Przykład

Ten przykład przedstawia ostatni krok w instalacji wersji programu Visual Studio, który zawiera pakiety VSPackage.

```
devenv /setup
```

## <a name="see-also"></a>Zobacz także

[Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)