---
title: "Modyfikowanie przy użyciu programu Isolated Shell. Pliku Vsct | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode, .vsct file
ms.assetid: 6d147c2d-10e9-400e-b8ce-5566287b41ba
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fcdaab4c5c9f0ee5522ae372e4a0cd94fb113eed
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="modifying-the-isolated-shell-by-using-the-vsct-file"></a>Modyfikowanie przy użyciu programu Isolated Shell. Plik Vsct
Projekt interfejsu użytkownika dla projektu programu Visual Studio programu isolated shell zawiera pliku vsct, co pozwala określić, które grupy aplikacji i poszczególnych polecenia są dostępne w aplikacji. Poniżej przedstawiono fragment pliku vsct bez modyfikacji.  
  
```  
<!-- <Define name="No_WindowListCommand"/> -->  
<!-- <Define name="No_MoreWindowsCommand"/> -->  
<!-- <Define name="No_PaneNextPaneCommand"/> -->  
<!-- <Define name="No_PanePrevPaneCommand"/> -->  
```  
  
 Domyślnie większość poleceń i polecenia grupy są dołączone. Aby wykluczyć polecenia lub grupy polecenia, po prostu usuń znaczniki komentarza tego polecenia lub grupy.  
  
 Na przykład, aby usunąć następne okienko i poprzednie okienko poleceń, usuń znaczniki komentarza `No_PaneNextPaneCommand` i `No_PanePrevPaneCommand` wpisy:  
  
```  
  
<Define name="No_PaneNextPaneCommand"/> <Define name="No_PanePrevPaneCommand"/>  
  
```  
  
 Aby uzyskać bardziej szczegółowe przykład te modyfikacje, zobacz [wskazówki: Tworzenie podstawowych izolowanych aplikacji powłoki](walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="referenced-files"></a>Plików  
 Następujące pliki odwołuje się do domyślnego pliku vsct dla aplikacji. Te pliki znajdują się w podkatalogu \VisualStudioIntegration\Common\Inc\ katalogu instalacyjnego programu Visual Studio SDK.  
  
|Plik|Opis|  
|----------|-----------------|  
|wbids.h|Tożsamości interfejsu użytkownika dla pakietu przeglądanie sieci Web.|  
|AppIDCmdUsed.vsct|Polecenie Tabela podstawowe elementy interfejsu użytkownika programu Visual Studio.|  
|EmulatorCmdUsed.vsct|Polecenie Tabela Emacs i Brief elementy interfejsu użytkownika emulacji edytora.|  
|Vsdebugguids.h|Definiuje identyfikatory GUID poleceń, strona Opcje i inne funkcje debuger programu Visual Studio.|  
|VsDbgCmdUsed.vsct|Polecenie tabeli dla debugera.|  
  
 Plik AppIDCmdUsed.vsct zawiera elementy interfejsu użytkownika programu Visual Studio, oparte na symbole zdefiniowane w pliku vsct aplikacji.  
  
 Aby uzyskać więcej informacji, zobacz [projektowania tabeli polecenia XML (. Pliki Vsct)](../internals/designing-xml-command-table-dot-vsct-files.md) i [odwołanie do schematu VSCT XML](../vsct-xml-schema-reference.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio izolowane powłoki](visual-studio-isolated-shell.md)