---
title: Obsługa poleceń | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - command handling
ms.assetid: 78f67d92-77f7-45cb-ad75-6e3346379cc3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a155927bb69c55c15a06cb058692038c8b309a30
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2018
ms.locfileid: "39230872"
---
# <a name="command-handling"></a>Obsługa poleceń
Edytor mogą definiować nowych poleceń. Polecenia są zwykle wyświetlane w menu na pasku narzędzi lub menu kontekstowego.  
  
 Aby uzyskać więcej informacji na temat definiowania menu i poleceń, zobacz [polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Usługa języka można kontrolować, jakie menu kontekstowe są wyświetlane w edytorze przechwycenie <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> wyliczenia. Alternatywnie można kontrolować menu kontekstowego na podstawie poszczególnych znacznika. Aby uzyskać więcej informacji, zobacz [ważne polecenia dotyczące filtrów usługi językowej](../extensibility/internals/important-commands-for-language-service-filters.md).  
  
## <a name="add-commands-to-the-editor-context-menu"></a>Dodawanie poleceń do menu kontekstowe edytora  
 Aby dodać polecenie do menu kontekstowego, należy najpierw zdefiniować zestaw poleceń menu należących do określonej grupy. Poniższy przykład pochodzi z *vsct* pliku generowanego w ramach tego przewodnika [wskazówki: Dodawanie funkcji do edytora niestandardowego](../extensibility/walkthrough-adding-features-to-a-custom-editor.md):  
  
 \<Menu identyfikator guid = "guidCustomEditorCmdSet" id = "IDMX_RTF" priorytet = "0x0000" type = "Kontekst" >  
  
 \<Nadrzędny identyfikator guid = "guidCustomEditorCmdSet" id = "0" / >  
  
 \<Ciągi >  
  
 \<ButtonText > Menu kontekstowe CustomEditor\</ButtonText >  
  
 \<CommandName > CustomEditorContextMenu\</CommandName >  
  
 \</ Ciągi >  
  
 \</ Menu >  
  
 \</ Menu >  
  
 Tekst powyżej dodaje polecenia menu kontekstowego tekstem **Menu kontekstowe CustomEditor**. Identyfikator GUID Menu jest częścią zestawu poleceń, które są tworzone za pomocą tego edytora. Typ to "Kontekst".  
  
 Można również użyć wstępnie zdefiniowanego polecenia, które nie muszą być zdefiniowane w *vsct* pliku. Na przykład sprawdzić *EditorPane.cs* pliku wygenerowanego przez szablon pakietu Visual Studio. Będzie zauważysz, że zestaw wstępnie zdefiniowanych poleceń, takich jak <xref:Microsoft.VisualStudio.VSConstants.VSStd97CmdID> definicją <xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>, są obsługiwane w programy obsługi poleceń, takich jak `onSelectAll` metody.  
  
## <a name="see-also"></a>Zobacz także  
 [Polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md)