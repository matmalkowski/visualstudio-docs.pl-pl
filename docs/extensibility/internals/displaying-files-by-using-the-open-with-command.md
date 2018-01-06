---
title: "Wyświetlanie plików przy użyciu Otwórz za pomocą polecenia | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project types, supporting Open With command
- Open With command
- persistence, supporting Open With command
ms.assetid: 53794bc3-1b73-4d40-954e-cfade1abddcf
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a1631632a2ceb66380d1d0c41e54b5a4244a31a3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="displaying-files-by-using-the-open-with-command"></a>Wyświetlanie plików przy użyciu Otwórz za pomocą polecenia
Projekt można zadawać IDE, aby wyświetlić **Otwórz za pomocą** okno dialogowe. To żądanie monituje użytkownika o otwarcie pliku, który ma wybór standardowe edytory. W poniższych krokach opisano tego procesu.  
  
1.  Wywołania projektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>, określając wartość OSE_UseOpenWithDialog dla `OSEOpenDocEditor` parametru.  
  
2.  Oparte na rozszerzenie nazwy pliku dokumentu, określa, które edytory wymienionych w rejestrze można otworzyć określonego dokumentu IDE i wyświetla te informacje w **Otwórz za pomocą** okno dialogowe.  
  
    > [!NOTE]
    >  Projekty, które edytora wewnętrzne, które muszą być zawarte w **Otwórz za pomocą** okno dialogowe Zarejestruj fabrykę edytora dla każdej z takich edytora. Edytory wewnętrzne tylko funkcji wraz z określonego typu projektu, który jest wymuszany w implementacji <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metody. IDE ma fabryki edytora wbudowanego edytora tekstów rdzeni i Edytor plików binarnych. IDE również tworzy wystąpienie fabryki edytora imieniu każdego zarejestrowanego skojarzenia plików systemu Windows. Przykładem takiego pliku jest program Microsoft Word.  
  
3.  Jak użytkownik wybiera element **Otwórz za pomocą** dokumentu zostanie otwarte okno dialogowe, następnie IDE przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metody. Aby uzyskać więcej informacji, zobacz [porady: otwieranie standardowe edytory](../../extensibility/how-to-open-standard-editors.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Otwieranie i zapisywanie elementów projektu](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Wyświetlanie plików za pomocą polecenia Otwórz plik](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)   
 [Instrukcje: otwieranie standardowych edytorów](../../extensibility/how-to-open-standard-editors.md)