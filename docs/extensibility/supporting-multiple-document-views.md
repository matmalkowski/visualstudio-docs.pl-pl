---
title: "Obsługa wielu widoków dokumentu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], custom - multiple document views
ms.assetid: c7ec2366-91c4-477f-908d-e89068bdb3e3
caps.latest.revision: "25"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 4efd76830356996bdf75c923f457d19d2381763c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="supporting-multiple-document-views"></a>Obsługa wielu widoków dokumentu
Musisz podać więcej niż jeden widok dokumentu przez utworzenie oddzielnych dokumentu danych i obiektów widoku dokumentu tego edytora. Niektórych przypadkach, w których byłoby widok dokumentu dodatkowe są:  
  
-   Nowa funkcja obsługi okna: ma edytora, aby zapewnić co najmniej dwa widoki tego samego typu, dzięki czemu użytkownik, który jest już otwarte w edytorze okna można otworzyć nowe okno, wybierając **nowe okno** polecenie **okna** menu.  
  
-   Formularz i kod Wyświetlanie pomocy technicznej: ma edytora, aby zapewnić widoków o różnych typach. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], na przykład obejmuje zarówno w widoku formularza, jak i w widoku kodu.  
  
 Aby uzyskać więcej informacji na ten temat zobacz procedurę CreateEditorInstance w pliku EditorFactory.cs w projekcie niestandardowego edytora utworzone przez szablon pakietu Visual Studio. Aby uzyskać więcej informacji na temat tego projektu, zobacz [wskazówki: tworzenie edytora niestandardowego](../extensibility/walkthrough-creating-a-custom-editor.md).  
  
## <a name="synchronizing-views"></a>Synchronizowanie widoków  
 Podczas implementowania wiele widoków, obiekt danych dokumentu jest musi zachować wszystkie widoki zsynchronizowane z danymi. Można użyć obsługi interfejsy na zdarzeń <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> zsynchronizować wiele widoków z danymi.  
  
 Jeśli nie używasz <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> obiektu do synchronizowania wiele widoków, a następnie musi implementować własny system zdarzeń obsługiwać zmiany do obiektu danych dokumentu. Korzystając z różną szczegółowością aktualności wiele widoków. Ustawienie maksymalnej szczegółowości podczas wpisywania, w jednym widoku inne widoki są natychmiast zaktualizować. Innych widoków z minimalny poziom szczegółowości, nie zostaną zaktualizowane, dopóki ich aktywacji.  
  
## <a name="determining-whether-document-data-is-already-open"></a>Określanie, czy dane dokumentu jest już otwarty  
 Uruchomionej tabeli dokumentu (Normalizacją) w zintegrowane środowisko programistyczne (IDE) pomaga sprawdzić, czy dane dokumentu jest już otwarty, jak pokazano na poniższym diagramie.  
  
 ![DocDataView — grafika](../extensibility/media/docdataview.gif "DocDataView —")  
Wiele widoków  
  
 Domyślnie każdy widok (obiekt widoku dokument) znajduje się w ramki okna (<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>). Jak już zanotowane, jednak dokumentu dane mogą być wyświetlane w wielu widoków. Aby włączyć tę opcję, Visual Studio sprawdza Normalizacją, aby określić, czy danego dokumentu jest już otwarty w edytorze. Gdy wywołuje IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> do tworzenia edytora, wartość inną niż NULL zwracane w `punkDocDataExisting` parametr wskazuje, że dokument jest już otwarty w innym edytorze. Aby uzyskać więcej informacji na temat funkcji Normalizacją zobacz [systemem tabeli dokumentu](../extensibility/internals/running-document-table.md).  
  
 W Twojej <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> implementacji badają obiekt danych dokumentu zwracane w `punkDocDataExisting` do ustalenia, czy dane dokumentu jest odpowiedni dla edytora. (Na przykład tylko dane HTML powinna być wyświetlana w przez edytor HTML.) Jeśli jest to odpowiednie, fabryką edytora powinien zapewnić drugi widok do danych. Jeśli `punkDocDataExisting` parametr nie jest `NULL`, istnieje możliwość, albo czy obiekt danych dokumentu jest otwarty w innym edytorze lub, bardziej prawdopodobne, dane dokumentu jest już otwarty w innym widoku o tym samym edytora. Jeśli dane dokumentu jest otwarty w edytorze różnych fabryką edytora nie obsługuje, Visual Studio nie można otworzyć fabryką edytora. Aby uzyskać więcej informacji, zobacz [porady: dołączanie widoków danych dokumentu](../extensibility/how-to-attach-views-to-document-data.md).