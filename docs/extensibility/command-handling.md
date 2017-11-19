---
title: "Obsługa poleceń | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - command handling
ms.assetid: 78f67d92-77f7-45cb-ad75-6e3346379cc3
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0cb2bf52c038b0abbac742aafa942f2f7ea7ea1d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="command-handling"></a>Obsługa poleceń
Edytor można zdefiniować nowe polecenia. Polecenia są zwykle wyświetlane w menu na pasku narzędzi lub w menu kontekstowym.  
  
 Aby uzyskać więcej informacji na temat definiowania menu i poleceń, zobacz [polecenia, menu i pasków narzędzi](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Usługa języka można kontrolować, jakie menu kontekstowe są wyświetlane w edytorze przechwycenie <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> wyliczenia. Alternatywnie można kontrolować menu kontekstowego w zasadzie na znacznika. Aby uzyskać więcej informacji, zobacz [ważne poleceń dla filtrów usługi języka](../extensibility/internals/important-commands-for-language-service-filters.md).  
  
## <a name="adding-commands-to-the-editor-context-menu"></a>Dodawanie poleceń do Menu kontekstowe edytora  
 Aby dodać polecenia do menu kontekstowego, należy określić zestaw poleceń menu należących do określonej grupy. Poniższy przykład pochodzi z pliku vsct wygenerowane w ramach tego przewodnika, [wskazówki: Dodawanie funkcji do edytora niestandardowego](../extensibility/walkthrough-adding-features-to-a-custom-editor.md):  
  
 \<Identyfikator guid menu = "guidCustomEditorCmdSet" id = "IDMX_RTF" priorytet = "0x0000" type = "Context" >  
  
 \<Nadrzędny identyfikator guid = "guidCustomEditorCmdSet" id = "0" / >  
  
 \<Ciągi >  
  
 \<ButtonText > Menu kontekstowe CustomEditor\</ButtonText >  
  
 \<CommandName > CustomEditorContextMenu\</CommandName >  
  
 \</ Ciągi >  
  
 \</ Menu >  
  
 \</ Menu >  
  
 Powyższy tekst dodaje polecenia menu kontekstowe tekstem **Menu kontekstowe CustomEditor**. Identyfikator GUID Menu jest zestawu poleceń, które jest tworzone z tego edytora, czy typ to "Context".  
  
 Można również użyć wstępnie zdefiniowanych poleceń, które nie muszą być zdefiniowane w pliku vsct. Na przykład, jeśli w pliku EditorPane.cs generowane przez szablon pakietu Visual Studio stwierdzisz, że zestaw wstępnie zdefiniowanych poleceń, takich jak <xref:Microsoft.VisualStudio.VSConstants.VSStd97CmdID> zdefiniowane przez <xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>, są obsługiwane w programy obsługi poleceń, takich jak metoda onSelectAll.  
  
## <a name="see-also"></a>Zobacz też  
 [Polecenia, menu i pasków narzędzi](../extensibility/internals/commands-menus-and-toolbars.md)