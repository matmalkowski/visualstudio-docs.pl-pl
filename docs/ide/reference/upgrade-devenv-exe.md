---
title: -Uaktualnienia (devenv.exe) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- /upgrade Devenv switch
- Devenv, /upgrade switch
- upgrade Devenv switch
ms.assetid: 3468045c-5cc9-4157-9a9d-622452145d27
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4e765d376276c6e83d7e2bcce2ab46974210d96c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="upgrade-devenvexe"></a>/Upgrade (devenv.exe)
Aktualizuje plik rozwiązania i wszystkie jego pliki projektu lub pliku projektu określony do bieżącego [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] formaty tych plików.  
  
## <a name="syntax"></a>Składnia  
  
```  
devenv SolutionFile | ProjectFile /upgrade  
```  
  
## <a name="arguments"></a>Argumenty  
 `SolutionFile`  
 Wymagane, jeśli uaktualnienie całego rozwiązania i jego projekty. Ścieżka i nazwa pliku rozwiązania. Można wprowadzić tylko nazwę pliku rozwiązania lub pełną ścieżkę i nazwę pliku rozwiązania. Folder lub plik o nazwie jeszcze nie istnieje, zostanie utworzona.  
  
 `ProjectFile`  
 Wymagane, Jeśli uaktualniasz pojedynczego projektu. Ścieżka i nazwa pliku projektu w ramach rozwiązania. Można wprowadzić tylko nazwę pliku projektu lub pełną ścieżkę i nazwę pliku projektu. Folder lub plik o nazwie jeszcze nie istnieje, zostanie utworzona.  
  
## <a name="remarks"></a>Uwagi  
 Kopie zapasowe są automatycznie tworzone i kopiowane do katalogu o nazwie kopii zapasowej, która jest tworzona w bieżącym katalogu.  
  
 Kontrolowane przez źródło rozwiązań lub projektów musi być wyewidencjonowany zanim można uaktualnić.  
  
 Przy użyciu `/upgrade` przełącznika nie można uruchomić [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Wyniki uaktualnienia można zobaczyć w raporcie uaktualnienia języka programowania rozwiązanie lub projekt. Brak informacji o błąd lub użycia są zwracane. Aby uzyskać więcej informacji na temat uaktualniania projektów w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], zobacz [portu, migracji i uaktualniania projektów programu Visual Studio](../../porting/port-migrate-and-upgrade-visual-studio-projects.md).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie uaktualnia plik rozwiązania o nazwie "MyProject.sln" w folderze domyślnym dla [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] rozwiązania.  
  
```  
devenv "MyProject.sln" /upgrade  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)