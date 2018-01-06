---
title: Tabela polecenia programu Visual Studio (. Pliki Vsct) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT files, overview
- Visual Studio command table configuration files (VSCT), overview
ms.assetid: 1313adb4-add4-4e74-90e2-f4be522f5259
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 71a202bdb71469e4d6b46eb537147092b1ea9013
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="visual-studio-command-table-vsct-files"></a>Tabela polecenia programu Visual Studio (. Pliki Vsct)
Plik konfiguracji tabeli polecenia to plik tekstowy, który opisuje zestaw poleceń, które zawiera pakiet VSPackage. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Polecenia kompilatora tabeli (VSCT) kompiluje konfiguracji w formacie XML plików (vsct) do plików wyjściowych (.cto) tabeli polecenie binary. Pliki wynikowe .cto są takie same jak te, które są tworzone za pomocą polecenia kompilatora tabeli (CTC) do kompilowania plików konfiguracyjnych .ctc. Pliki vsct opartych na języku XML ma jednak pewne korzyści, takich jak edytor XML i XML IntelliSense.  
  
 Aby dowiedzieć się więcej na temat składni i semantyki vsct plików, zobacz [projektowania tabeli polecenia XML (. Pliki Vsct)](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Projektowanie tabeli poleceń XML (pliki Vsct)](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
 Opisuje sposób projektowania vsct plików.  
  
 [Instrukcje: tworzenie pliku Vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)  
 Porównanie metod tworzenia pliku vsct. W tym artykule opisano proces ręcznego tworzenia nowego pliku vsct.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Odwołanie do schematu XML VSCT](../../extensibility/vsct-xml-schema-reference.md)  
 Szczegółowe informacje na temat każdej sekcji pliku konfiguracji XML tabeli poleceń.  
  
 [Polecenie konfiguracją tabeli (. Pliki CTC)](http://msdn.microsoft.com/en-us/3413dda1-f372-4669-bcf0-c64d3463842c)  
 Zawiera omówienie formatu pliku .ctc przestarzałe.  
  
 [Dodawanie elementów interfejsu użytkownika przy użyciu pakietów VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 W tym artykule opisano specyfikacji formatu tabeli polecenia.  
  
 [Zasoby w pakietach VSPackage](../../extensibility/internals/resources-in-vspackages.md)  
 Opis sposobu użycia zasobów zarządzanych i niezarządzanych w zarządzanych VSPackages.  
  
 [Polecenia, menu i paski narzędzi](../../extensibility/internals/commands-menus-and-toolbars.md)  
 Wyjaśnia sposób tworzenia interfejsu użytkownika, który zawiera menu, paski narzędzi i polecenia pola kombi.