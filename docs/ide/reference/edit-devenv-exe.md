---
title: -Edytuj (devenv.exe) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Devenv, /edit switch
- /Edit Devenv swtich
ms.assetid: 02b3d6e7-a2b1-4d83-a747-aa8c2fb758b7
caps.latest.revision: "6"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 34b256a788f2ce8077d7f62921a63565f210139a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="edit-devenvexe"></a>/Edit (devenv.exe)
Otwiera określony plik w istniejącym wystąpieniem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="syntax"></a>Składnia  
  
```  
Devenv /edit [file1[ file2]]  
```  
  
## <a name="arguments"></a>Argumenty  
 `file1`  
 Opcjonalny. Plik można otworzyć w istniejącym wystąpieniem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Jeśli żadne wystąpienie elementu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] istnieje, jest tworzone nowe wystąpienie o układ okna uproszczony, i `file1` jest otwarty w tym nowym wystąpieniu.  
  
 `file2`  
 Opcjonalny. Co najmniej jeden dodatkowe pliki można otworzyć w istniejącego wystąpienia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="remarks"></a>Uwagi  
 Jeśli nie określono żadnych pliku i Brak istniejącego wystąpienia programu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], istniejącego wystąpienia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] uzyskuje fokus. Jeśli nie określono żadnych pliku i nie żadne istniejące wystąpienie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], nowe wystąpienie klasy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jest tworzony z układem uproszczony okna.  
  
 Jeśli istniejącego wystąpienia programu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jest w stanie modalne, na przykład, jeśli [opcje — Okno dialogowe](../../ide/reference/options-dialog-box-visual-studio.md) jest otwarta, plik zostanie otwarte w istniejące wystąpienie kiedy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] opuszcza stan modalny.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie otwiera plik `MyFile.cs` w istniejącym wystąpieniem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] lub otwiera plik w nowe wystąpienie klasy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Jeśli już nie istnieje.  
  
```  
devenv /edit MyFile.cs  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)