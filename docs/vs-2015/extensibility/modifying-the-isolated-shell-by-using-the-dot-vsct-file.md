---
title: Modyfikowanie programu Isolated Shell przy użyciu. Pliku Vsct | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C .vsct file
ms.assetid: 6d147c2d-10e9-400e-b8ce-5566287b41ba
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0606d28f151f0d9c85980121e3129bd9204c61b8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42688787"
---
# <a name="modifying-the-isolated-shell-by-using-the-vsct-file"></a>Modyfikowanie programu Isolated Shell przy użyciu. Pliku Vsct
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [modyfikowanie izolowane powłoki za pomocą. Pliku Vsct](https://docs.microsoft.com/visualstudio/extensibility/modifying-the-isolated-shell-by-using-the-dot-vsct-file).  
  
Projekt interfejsu użytkownika dla projektu programu Visual Studio shell w trybie izolowanym zawiera pliku vsct, co pozwala określić, które grupy aplikacji i poszczególne polecenia są dostępne w aplikacji. Poniżej przedstawiono fragment pliku vsct zostały zmodyfikowane.  
  
```  
<!-- <Define name="No_WindowListCommand"/> -->  
<!-- <Define name="No_MoreWindowsCommand"/> -->  
<!-- <Define name="No_PaneNextPaneCommand"/> -->  
<!-- <Define name="No_PanePrevPaneCommand"/> -->  
```  
  
 Domyślnie większość poleceń i polecenia grupy uwzględniono. Aby wykluczyć polecenia lub grupy poleceń, po prostu usuń znaczniki komentarza tego polecenia lub grupy.  
  
 Na przykład, aby usunąć następne okienko i poprzednie okienko polecenia, usuń znaczniki komentarza `No_PaneNextPaneCommand` i `No_PanePrevPaneCommand` wpisy:  
  
```  
  
<Define name="No_PaneNextPaneCommand"/> <Define name="No_PanePrevPaneCommand"/>  
  
```  
  
 Aby uzyskać bardziej szczegółowy przykład dostosowania, zobacz [wskazówki: Tworzenie podstawowej aplikacji izolowanej powłoki](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="referenced-files"></a>Pliki z odwołaniami  
 Następujące pliki odwołuje się do domyślnego pliku vsct dla aplikacji. Te pliki znajdują się w podkatalogu \VisualStudioIntegration\Common\Inc\ katalogu instalacyjnego programu Visual Studio SDK.  
  
|Plik|Opis|  
|----------|-----------------|  
|wbids.h|Tożsamości interfejsu użytkownika dla przeglądania sieci Web pakietu.|  
|AppIDCmdUsed.vsct|Tabela polecenia podstawowe elementy interfejsu użytkownika usługi Visual Studio.|  
|EmulatorCmdUsed.vsct|Tabela polecenia Emacs i krótki opis elementów interfejsu użytkownika emulacji edytora.|  
|Vsdebugguids.h|Określa identyfikator GUID w faktycznej poleceń, Strona opcji i inne funkcje debugera programu Visual Studio.|  
|VsDbgCmdUsed.vsct|Tabeli poleceń w debugerze.|  
  
 Plik AppIDCmdUsed.vsct zawiera elementy interfejsu użytkownika usługi Visual Studio, oparte na symbole zdefiniowane w pliku vsct aplikacji.  
  
 Aby uzyskać więcej informacji, zobacz [projektowanie tabeli poleceń XML (. Pliki Vsct)](../extensibility/internals/designing-xml-command-table-dot-vsct-files.md) i [odwołanie do schematu VSCT XML](../extensibility/vsct-xml-schema-reference.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio Isolated Shell](../extensibility/visual-studio-isolated-shell.md)

