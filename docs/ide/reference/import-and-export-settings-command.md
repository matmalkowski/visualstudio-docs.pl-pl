---
title: "Import i eksport ustawień — polecenie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d4337a5755a58c03c827849417412885f42127a0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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
 Uruchomienie tego polecenia, których nie zmienia otwiera **Import i eksport ustawień** kreatora. Aby uzyskać więcej informacji, zobacz [porady: ustawienia udziału między komputerami lub wersji programu Visual Studio](http://msdn.microsoft.com/en-us/1131fb10-35c1-42da-9cd8-91aa3235b882).  
  
## <a name="example"></a>Przykład  
 Polecenie eksportuje bieżące ustawienia do pliku `MyFile.vssettings`.  
  
```  
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Personalizowanie środowiska IDE programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)   
 [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)