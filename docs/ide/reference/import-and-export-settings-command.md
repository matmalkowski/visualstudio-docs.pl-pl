---
title: Import i eksport ustawień — polecenie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
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
ms.openlocfilehash: ad7da7f8d83cd45e7cc7801d430dbf70887747b3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="import-and-export-settings-command"></a>Import i eksport ustawień — Polecenie
Importuje eksportuje i resetuje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ustawienia.  
  
## <a name="syntax"></a>Składnia  
  
```  
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]  
```  
  
## <a name="switches"></a>Przełączniki  
 / export:`filename`  
 Opcjonalny. Eksportuje bieżące ustawienia do określonego pliku.  
  
 / Import:`filename`  
 Opcjonalny. Importuje ustawienia w określonym pliku.  
  
 / Reset  
 Opcjonalny. Przywraca bieżące ustawienia.  
  
## <a name="remarks"></a>Uwagi

Uruchomienie tego polecenia, których nie zmienia otwiera **Import i eksport ustawień** kreatora. Aby uzyskać więcej informacji, zobacz [synchronizację ustawień](../../ide/synchronized-settings-in-visual-studio.md).

## <a name="example"></a>Przykład

Polecenie eksportuje bieżące ustawienia do pliku `MyFile.vssettings`.

```shell
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"
```

## <a name="see-also"></a>Zobacz także

[Personalizowanie środowiska IDE programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)  
[Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)