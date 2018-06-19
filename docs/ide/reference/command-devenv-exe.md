---
title: -Command (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /command switch
- /command Devenv switch
ms.assetid: 13c20cd6-f09d-400a-8b7b-ecc266a32cef
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c21402c3b2b71372aaf170c68c65777eba4e95bf
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33703749"
---
# <a name="command-devenvexe"></a>/Command (devenv.exe)
Wykonuje określone polecenie po uruchomieniu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zintegrowane środowisko programistyczne (IDE).

## <a name="syntax"></a>Składnia

```cmd
devenv /command CommandName
```

## <a name="arguments"></a>Argumenty
 `CommandName` Wymagane. Pełna nazwa [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] polecenia lub jego alias ujęta w znaki podwójnego cudzysłowu. Aby uzyskać więcej informacji o poleceniu i alias składni, zobacz [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md).

## <a name="remarks"></a>Uwagi
 Po zakończeniu uruchamiania IDE wykonuje polecenie nazwanego. Jeśli używasz tego przełącznika nie wyświetla IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] strony początkowej podczas uruchamiania.

 Jeśli dodatek udostępnia polecenia, korzystając tego przełącznika można uruchomić z wiersza polecenia dodatku. Aby uzyskać więcej informacji, zobacz [porady: kontrolki dodatki za pomocą Menedżera dodatków](http://msdn.microsoft.com/Library/4f60444a-cb48-4cdb-8df4-941f6419aeeb).

## <a name="example"></a>Przykład
 W tym przykładzie uruchamia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] i automatycznie uruchamia makro otwartych plików ulubionych.

```cmd
devenv /command "Macros.MyMacros.Module1.OpenFavoriteFiles"
```

## <a name="see-also"></a>Zobacz też

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)