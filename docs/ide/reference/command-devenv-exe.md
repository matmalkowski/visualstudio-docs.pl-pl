---
title: -Command (devenv.exe) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Devenv, /command switch
- /command Devenv switch
ms.assetid: 13c20cd6-f09d-400a-8b7b-ecc266a32cef
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6f7f2914b59025d3cf1dc82d43191f43ec7b0115
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="command-devenvexe"></a>/Command (devenv.exe)
Wykonuje określone polecenie po uruchomieniu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zintegrowane środowisko programistyczne (IDE).  
  
## <a name="syntax"></a>Składnia  
  
```  
devenv /command CommandName  
```  
  
## <a name="arguments"></a>Argumenty  
 `CommandName`  
 Wymagany. Pełna nazwa [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] polecenia lub jego alias ujęta w znaki podwójnego cudzysłowu. Aby uzyskać więcej informacji o poleceniu i alias składni, zobacz [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md).  
  
## <a name="remarks"></a>Uwagi  
 Po zakończeniu uruchamiania IDE wykonuje polecenie nazwanego. Jeśli używasz tego przełącznika nie wyświetla IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] strony początkowej podczas uruchamiania.  
  
 Jeśli dodatek udostępnia polecenia, korzystając tego przełącznika można uruchomić z wiersza polecenia dodatku. Aby uzyskać więcej informacji, zobacz [porady: kontrolki dodatki za pomocą Menedżera dodatków](http://msdn.microsoft.com/Library/4f60444a-cb48-4cdb-8df4-941f6419aeeb).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie uruchamia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] i automatycznie uruchamia makro otwartych plików ulubionych.  
  
```  
devenv /command "Macros.MyMacros.Module1.OpenFavoriteFiles"  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)