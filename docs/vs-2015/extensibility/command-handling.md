---
title: Obsługa poleceń | Dokumentacja firmy Microsoft
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
- editors [Visual Studio SDK], legacy - command handling
ms.assetid: 78f67d92-77f7-45cb-ad75-6e3346379cc3
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 32bfe8ec88d0e2ad5a2b765dcff01f543fe59c18
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42677136"
---
# <a name="command-handling"></a>Obsługa poleceń
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [obsługi polecenia](https://docs.microsoft.com/visualstudio/extensibility/command-handling).  
  
Edytor mogą definiować nowych poleceń. Polecenia są zwykle wyświetlane w menu na pasku narzędzi lub menu kontekstowego.  
  
 Aby uzyskać więcej informacji na temat definiowania menu i poleceń, zobacz [polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Usługa języka można kontrolować, jakie menu kontekstowe są wyświetlane w edytorze przechwycenie <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> wyliczenia. Alternatywnie można kontrolować menu kontekstowego na podstawie poszczególnych znacznika. Aby uzyskać więcej informacji, zobacz [ważne polecenia dotyczące filtrów usługi językowej](../extensibility/internals/important-commands-for-language-service-filters.md).  
  
## <a name="adding-commands-to-the-editor-context-menu"></a>Dodawanie poleceń do Menu kontekstowe edytora  
 Aby dodać polecenie do menu kontekstowego, należy najpierw zdefiniować zestaw poleceń menu należących do określonej grupy. Poniższy przykład pochodzi z pliku vsct wygenerowane jako część tego przewodnika [wskazówki: Dodawanie funkcji do edytora niestandardowego](../extensibility/walkthrough-adding-features-to-a-custom-editor.md):  
  
 \<Menu identyfikator guid = "guidCustomEditorCmdSet" id = "IDMX_RTF" priorytet = "0x0000" type = "Kontekst" >  
  
 \<Nadrzędny identyfikator guid = "guidCustomEditorCmdSet" id = "0" / >  
  
 \<Ciągi >  
  
 \<ButtonText > Menu kontekstowe CustomEditor\</ButtonText >  
  
 \<CommandName > CustomEditorContextMenu\</CommandName >  
  
 \</ Ciągi >  
  
 \</ Menu >  
  
 \</ Menu >  
  
 Tekst powyżej dodaje polecenia menu kontekstowego tekstem **Menu kontekstowe CustomEditor**. Identyfikator GUID Menu jest zestawu poleceń, które jest tworzone za pomocą tego edytora, a typ to "Kontekst".  
  
 Można również użyć wstępnie zdefiniowanego polecenia, które nie muszą być zdefiniowane w pliku vsct. Na przykład jeśli zapoznaj się z plikiem EditorPane.cs, generowane przez szablon pakietu Visual Studio, zauważysz, że zestaw wstępnie zdefiniowanych poleceń, takich jak <xref:Microsoft.VisualStudio.VSConstants.VSStd97CmdID> definicją <xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>, są obsługiwane w programy obsługi poleceń, takich jak metoda onSelectAll.  
  
## <a name="see-also"></a>Zobacz też  
 [Polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md)

