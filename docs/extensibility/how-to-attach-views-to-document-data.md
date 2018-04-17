---
title: 'Porady: dołączanie widoków danych dokumentów | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - attach views to document data
ms.assetid: f92c0838-45be-42b8-9c55-713e9bb8df07
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e3dfe0163bc4a47ec51e5c2dea832f6adda42ff7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-attach-views-to-document-data"></a>Porady: dołączanie widoków danych dokumentów
Jeśli masz nowy widok dokumentu, można dołączyć do istniejącego obiektu danych dokumentu.  
  
### <a name="to-determine-if-you-can-attach-a-view-to-an-existing-document-data-object"></a>Aby określić, czy widok można dołączyć do istniejącego obiektu danych dokumentu  
  
1.  Implementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>.  
  
2.  W implementacji `IVsEditorFactory::CreateEditorInstance`, wywołaj `QueryInterface` na istniejący obiekt danych dokumentu, gdy wywołuje środowiska IDE programu `CreateEditorInstance` implementacji.  
  
     Wywoływanie `QueryInterface` umożliwia zbadania istniejącego obiektu danych dokumentu, która została określona w `punkDocDataExisting` parametru.  
  
     Dokładne interfejsów, które musisz wykonać kwerendę zależy edytorze, który jest otworzyć dokument, jednak zgodnie z opisem w kroku 4.  
  
3.  Jeśli nie możesz znaleźć odpowiednich interfejsów na istniejący obiekt danych dokumentu, zwracany jest kod błędu do edytora wskazująca, że obiekt danych dokumentu jest niezgodny z edytora.  
  
     W implementacji programu IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>, okno komunikatu informuje, że dokument jest otwarty w innym edytorze i zapyta, czy chcesz je zamknąć.  
  
4.  Jeśli ten dokument zostanie zamknięty, następnie Visual Studio wymaga fabryką edytora po raz drugi. Dla tego wywołania `DocDataExisting` parametru jest równa NULL. Wdrożenie fabryki edytora można otworzyć obiektu danych dokumentu w edytorze własne.  
  
    > [!NOTE]
    >  Aby ustalić, czy możesz pracować z istniejącego obiektu danych dokumentu, umożliwia także prywatnej znajomości implementacji interfejsu przez rzutowanie wskaźnika do rzeczywistej [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] klasy prywatnej implementacji. Na przykład wprowadzić wszystkie standardowe edytory `IVsPersistFileFormat`, który dziedziczy z <xref:Microsoft.VisualStudio.OLE.Interop.IPersist>. W związku z tym można wywołać `QueryInterface` dla <xref:Microsoft.VisualStudio.OLE.Interop.IPersist.GetClassID%2A>, i czy identyfikator klasy istniejącego dokumentu obiektu danych zgodne z implementacji identyfikator klasy, a następnie możesz pracować z obiektem danych dokumentu.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Gdy program Visual Studio wymaga implementacji <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metody przekazaniem wstecz wskaźnik do istniejącego obiektu danych dokumentu w `punkDocDataExisting` parametru, jeśli taka istnieje. Badają obiekt danych dokumentu zwracane w `punkDocDataExisting` do ustalenia, czy obiekt danych dokumentu jest odpowiedni dla edytora w sposób opisany w nocie w kroku 4 procedury w tym temacie. Jeśli jest to odpowiednie, a następnie fabryką edytora powinien zapewnić drugi widok do danych w sposób opisany w [obsługi wielu widoków dokumentu](../extensibility/supporting-multiple-document-views.md). Jeśli nie, następnie należy wyświetlić odpowiedni komunikat o błędzie.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa wielu widoków dokumentu](../extensibility/supporting-multiple-document-views.md)   
 [Dane dokumentu i widok dokumentu w edytorach niestandardowych](../extensibility/document-data-and-document-view-in-custom-editors.md)