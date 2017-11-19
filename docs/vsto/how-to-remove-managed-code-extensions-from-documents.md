---
title: "Porady: Usuwanie rozszerzenia kodu zarządzanego z dokumentów | Dokumentacja firmy Microsoft"
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
- managed code extensions [Office development in Visual Studio], removing
- documents [Office development in Visual Studio], managed code extensions
ms.assetid: e893d9a5-72a5-4087-b81b-04d4d3d9ebf8
caps.latest.revision: "30"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f9da75468ae417bd835b457cdbd5219ef9462df1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-remove-managed-code-extensions-from-documents"></a>Porady: usuwanie rozszerzenia kodu zarządzanego z dokumentów
  Programowo można usunąć zestawu dostosowania z dokumentu lub skoroszytu, który jest częścią dostosowanie poziomie dokumentu dla programu Microsoft Office Word i Microsoft Office Excel. Użytkownicy mogą otwierać dokumenty i przeglądanie zawartości, ale nie będą wyświetlane wszystkie niestandardowego interfejsu użytkownika (UI) dodawanie do dokumentów i kod nie zostanie uruchomiona.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Można usunąć zestawu dostosowywania za pomocą jednej z metod RemoveCustomization dostarczonych przez [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Wybór metody zależy od tego, czy chcesz usunąć dostosowania w czasie wykonywania (uruchamiając kod na dostosowania podczas słowo skoroszytu programu Excel lub dokumentu jest otwarty), lub jeśli chcesz usunąć dostosowań z zamkniętego dokumentu lub że s na serwerze, który nie ma zainstalowanych w Microsoft Office.  
  
 ![łącze do wideo](../vsto/media/playvideo.gif "łącze do wideo") dla powiązanych pokaz wideo, zobacz [jak I: czy dołączać lub odłącz zestawem VSTO z dokumentu programu Word?](http://go.microsoft.com/fwlink/?LinkId=136782).  
  
### <a name="to-remove-the-customization-assembly-at-run-time"></a>Aby usunąć zestaw dostosowania w czasie wykonywania  
  
1.  W kodzie dostosowania wywołać <xref:Microsoft.Office.Tools.Word.Document.RemoveCustomization%2A> — metoda (dla programu Word) lub <xref:Microsoft.Office.Tools.Excel.Workbook.RemoveCustomization%2A> — metoda (dla programu Excel). Tę metodę należy wywoływać tylko wtedy, gdy dostosowania nie są już potrzebne.  
  
     Gdy ta metoda jest wywoływana w kodzie, zależy od tego, jak dostosowanie jest używana. Na przykład jeśli klientom korzystać z funkcji Twoje dostosowania dopóki nie będą gotowe do wysyłania dokumentu do innych klientów, którzy należy tylko w dokumencie (nie dostosowywania), musisz podać niektóre interfejsu użytkownika, który wywołuje RemoveCustomization po kliknięciu przez klienta. Alternatywnie Jeśli dostosowanie wypełnia dokument z danymi, po pierwszym otwarciu, ale dostosowania nie udostępnia inne funkcje, które są udostępniane bezpośrednio przez klientów, następnie można wywołać RemoveCustomization tak szybko, jak dostosowanie Zakończenie inicjowania dokumentu.  
  
### <a name="to-remove-the-customization-assembly-from-a-closed-document-or-a-document-on-a-server"></a>Aby usunąć zestaw dostosowania z zamkniętego dokumentu lub na serwerze  
  
1.  W projekcie, który nie wymaga programu Microsoft Office, takich jak aplikacji konsoli lub projektu formularzy systemu Windows i Dodaj odwołanie do zestawu Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll.  
  
2.  Dodaj następujące **importów** lub **przy użyciu** instrukcji na początku pliku kodu.  
  
     [!code-csharp[Trin_VstcoreDeployment#1](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#1)]
     [!code-vb[Trin_VstcoreDeployment#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#1)]  
  
3.  Wywołaj statycznych <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> metody <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> klasy, a następnie określ ścieżkę dokumentu rozwiązania dla parametru.  
  
     Poniższy przykład kodu zakłada spowoduje usunięcie dostosowań z dokumentu o nazwie **WordDocument1.docx** znajduje się na pulpicie.  
  
     [!code-csharp[Trin_VstcoreDeployment#2](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#2)]
     [!code-vb[Trin_VstcoreDeployment#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#2)]  
  
4.  Skompiluj projekt i uruchomić aplikację na komputerze, w której chcesz usunąć dostosowań. Komputer musi mieć Visual Studio 2010 Tools for Office Runtime zainstalowany.  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie dokumentami na serwerze za pomocą klasy ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Porady: dołączanie rozszerzenia kodu zarządzanego do dokumentów](../vsto/how-to-attach-managed-code-extensions-to-documents.md)  
  
  