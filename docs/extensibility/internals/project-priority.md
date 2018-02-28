---
title: Priorytet projektu | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: ae692249ea952970b096825c8f6968158eb2f17f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="project-priority"></a>Priorytet projektu
Element projektu zwykle jest elementem członkowskim tylko jednego projektu w rozwiązaniu. W związku z tym IDE może łatwo ustalić, który projekt jest używany do otwierania elementu. Jednak jeśli element jest członkiem więcej niż jeden projekt, IDE wykorzystuje schemat priorytet ustalenie najlepszych projektu do otwierania elementu.  
  
 Poniższa lista zawiera schemat priorytet projektu:  
  
-   Wywołania IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A> metody dla każdego projektu w rozwiązaniu do ustalenia, czy dokument jest członkiem tego projektu.  
  
-   Jeśli dokument jest elementem członkowskim projektu, projekt odpowiada priorytet czy projekt przypisuje zgodnie z jego obsługa tego dokumentu. Na przykład projektu języka odpowiada o wysokim priorytecie dla jego języka plików źródłowych, ale odpowiada o wyższym priorytecie typu nierozpoznany pliku, który nie jest używany jako część procesu kompilacji.  
  
-   Projekty, które zapewniają projektantów lub edytory niestandardowych, specyficzne dla projektu dla dokumentu również odbierać o wysokim priorytecie.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> Wyliczenie zawiera dokument wartości priorytetu.  
  
-   Projekt, który określa najwyższy priorytet znajduje się kontekst otworzyć dokument. Jeśli dwa projekty zwracają wartości w taki sam priorytet, preferowane jest aktywnego projektu. Jeśli żaden projekt w rozwiązaniu odpowiada, że można otworzyć dokumentu, IDE umieszcza dokumentu w projekcie różne pliki. Aby uzyskać więcej informacji, zobacz [projekt różne pliki](../../extensibility/internals/miscellaneous-files-project.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Projekt różne pliki](../../extensibility/internals/miscellaneous-files-project.md)   
 [Porady: Otwórz edytory dla otwarte dokumenty](../../extensibility/how-to-open-editors-for-open-documents.md)   
 [Dodawanie projektu i szablonów elementów projektu](../../extensibility/internals/adding-project-and-project-item-templates.md)