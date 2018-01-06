---
title: "Porady: dołączanie rozszerzenia kodu zarządzanego do dokumentów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- managed code extensions [Office development in Visual Studio], attaching
- documents [Office development in Visual Studio], managed code extensions
ms.assetid: b38c3a35-8b4a-4e86-8475-88fa8a873a5d
caps.latest.revision: "33"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: fe976923c77902a4e3e42fc634a3227cadccdfc5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-attach-managed-code-extensions-to-documents"></a>Porady: Dołączanie rozszerzenia kodu zarządzanego do dokumentów
  W zestawie dostosowania można dołączyć do istniejącego dokumentu Microsoft Office Word lub skoroszyt programu Microsoft Office Excel. Dokument lub skoroszyt można w dowolnym formacie, który jest obsługiwany przez program Microsoft Office projektów i narzędzia do programowania w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [architektura poziomie dokumentu](../vsto/architecture-of-document-level-customizations.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Aby dołączyć dostosowanie do dokumentu programu Word czy Excel, użyj <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> metody <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> klasy. Ponieważ <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> klasy jest przeznaczony do uruchamiania na komputerze, który nie ma Microsoft Office zainstalowany, możesz użyć tej metody w rozwiązaniach, które nie są bezpośrednio związane z programowanie Microsoft Office (na przykład konsoli lub w aplikacji formularzy systemu Windows).  
  
> [!NOTE]  
>  Dostosowanie nie będzie można załadować, jeśli kod oczekuje formantów, które nie mają określonego dokumentu.  
  
 ![łącze do wideo](../vsto/media/playvideo.gif "łącze do wideo") dla powiązanych pokaz wideo, zobacz [jak I: czy dołączać lub odłącz zestawem VSTO z dokumentu programu Word?](http://go.microsoft.com/fwlink/?LinkId=136782).  
  
### <a name="to-attach-managed-code-extensions-to-a-document"></a>Aby dołączanie rozszerzenia kodu zarządzanego do dokumentu  
  
1.  W projekcie, który nie wymaga programu Microsoft Office, takich jak aplikacji konsoli lub projektu formularzy systemu Windows, należy dodać odwołanie do Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll i Microsoft.VisualStudio.Tools.Applications.Runtime.dll zestawy.  
  
2.  Dodaj następujące **importów** lub **przy użyciu** instrukcje na początku pliku kodu.  
  
     [!code-csharp[Trin_VstcoreDeployment#4](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#4)]
     [!code-vb[Trin_VstcoreDeployment#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#4)]  
  
3.  Wywołaj statycznych <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> metody.  
  
     Poniższy przykład kodu wykorzystuje <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> przeciążenia. To przeciążenie przyjmuje pełną ścieżkę dokumentu i <xref:System.Uri> lokalizacji manifestu rozmieszczenia dostosowywania chcesz dołączyć do dokumentu. W tym przykładzie przyjęto założenie, że dokument programu Word o nazwie **WordDocument1.docx** znajduje się na pulpicie, oraz że manifest wdrażania znajduje się w folderze o nazwie **publikowania** to również na pulpicie.  
  
     [!code-csharp[Trin_VstcoreDeployment#3](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#3)]
     [!code-vb[Trin_VstcoreDeployment#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#3)]  
  
4.  Skompiluj projekt i uruchomić aplikację na komputerze, w których chcesz dołączyć dostosowań. Komputer musi mieć Visual Studio 2010 Tools for Office Runtime zainstalowany.  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie dokumentami na serwerze za pomocą klasy ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Porady: Usuwanie rozszerzenia kodu zarządzanego z dokumentów](../vsto/how-to-remove-managed-code-extensions-from-documents.md)   
 [Aplikacje i manifesty wdrożenia w rozwiązaniach pakietu Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)  
  