---
title: -ResetSkipPkgs (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /ResetSkipPkgs Devenv switch
- Devenv, /ResetSkipPkgs switch
- ResetSkipPkgs switch
ms.assetid: 7ece64f9-cfa4-4b34-b0d9-1c338b9557b3
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6199bf96bc631cf1018b2cb72a4d3c3cf7c703cc
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="resetskippkgs-devenvexe"></a>/ResetSkipPkgs (devenv.exe)
Czyści wszystkie opcje, aby pominąć ładowanie dodane do VSPackages przez użytkowników, które chcą uniknąć obciążania problem VSPackages, a następnie uruchamia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="syntax"></a>Składnia

```
Devenv /ResetSkipPkgs
```

## <a name="remarks"></a>Uwagi
 Obecność tagu SkipLoading wyłącza ładowanie pakiet VSPackage; ponownie wyczyszczenie tagu umożliwia ładowanie pakiet VSPackage.

## <a name="example"></a>Przykład
 Poniższy przykład czyści wszystkie tagi SkipLoading.

```
Devenv.exe /ResetSkipPkgs
```

## <a name="see-also"></a>Zobacz też

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)