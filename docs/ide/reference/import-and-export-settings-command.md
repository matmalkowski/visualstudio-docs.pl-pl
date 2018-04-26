---
title: Import i eksport ustawień — Polecenie
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a95841d9b9b8e67f34883efcc1a55a2daba7e8b7
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="import-and-export-settings-command"></a>Import i eksport ustawień — Polecenie
Importuje eksportuje i resetuje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ustawienia.

## <a name="syntax"></a>Składnia

```
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]
```

## <a name="switches"></a>Przełączniki
 / export:`filename`

 Opcjonalna. Eksportuje bieżące ustawienia do określonego pliku.

 / Import:`filename`

 Opcjonalna. Importuje ustawienia w określonym pliku.

 / Reset

 Opcjonalna. Przywraca bieżące ustawienia.

## <a name="remarks"></a>Uwagi

Uruchomienie tego polecenia, których nie zmienia otwiera **Import i eksport ustawień** kreatora. Aby uzyskać więcej informacji, zobacz [synchronizację ustawień](../../ide/synchronized-settings-in-visual-studio.md).

## <a name="example"></a>Przykład

Polecenie eksportuje bieżące ustawienia do pliku `MyFile.vssettings`.

```shell
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"
```

## <a name="see-also"></a>Zobacz także

- [Personalizowanie środowiska IDE programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)