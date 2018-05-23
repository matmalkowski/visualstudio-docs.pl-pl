---
title: Ochrona dokumentów w rozwiązaniach na poziomie dokumentu
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- restricted permissions [Office development in Visual Studio]
- permissions [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio], restricted permissions
- documents [Office development in Visual Studio], restricted permissions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 22c8f135770fbd427d361b9c9b113da3b20e609a
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2018
---
# <a name="document-protection-in-document-level-solutions"></a>Ochrona dokumentów w rozwiązaniach na poziomie dokumentu
  Można użyć funkcji ochrony w projektach na poziomie dokumentu Microsoft Office Word i Microsoft Office Excel. Te funkcje zablokować nieuprawnionym użytkownikom wprowadzanie zmian do części chronionego dokumentu.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Przy użyciu programu Excel, ochronę można włączyć lub wyłączyć gdy skoroszyt jest otwarty w projektancie. Za pomocą programu Word, można włączyć ochrony tylko poza projektantem. W czasie wykonywania można włączyć lub wyłączyć ochronę programowe dla programu Word i Excel.  
  
 Po włączeniu ochrony dokumentu na dokument, który jest otwarty w projektancie, wszystkie formanty są usuwane z **przybornika** lub staną się niedostępne, i nie można przeciągnąć nic **źródeł danych** okno w dokumencie.  
  
## <a name="serverdocument-and-protected-documents"></a>ServerDocument i chronione dokumenty  
 Jeśli dokument jest chroniony, pamięć podręczna danych nie są dostępne z poza dokumentu. Nie można użyć <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> klasy można pobrać lub manipulować danymi buforowaną chronionego dokumentu lub użyć innych metod <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument> klasy.  
  
## <a name="word-document-protection-in-the-designer"></a>Ochrona dokumentu programu Word w Projektancie  
 Jeśli dodasz ochrony do dokumentu programu Word lub szablonu, gdy jest on otwarty w programie Visual Studio, nie można rozpocząć Wymuszanie ochrony w projektancie. Dokument jest w trybie projektowania, gdy jest on otwarty w programie Visual Studio i go musi być w tryb uruchamiania przed rozpoczęciem wymuszania ochrony.  
  
 Jeśli tworzysz projekt, który korzysta z istniejącego dokumentu programu Word z włączoną ochroną, dokument jest chroniony otwarty w projektancie. Nie można edytować chronionych części dokumentu, ale możesz napisać kod w edytorze kodu można zautomatyzować dokumentu. Można również nie można skompilować projekt Jeśli włączono ochronę dokumentu jest otwarty w programie Visual Studio.  
  
 Można wyłączyć ochrony, gdy dokument jest otwarty w projektancie, dzięki czemu można edytować dokument i skompilować projekt. Nie można wyłączyć ochrony dla kopii w projektancie, podczas debugowania; dokument, który zostanie otwarty podczas debugowania jest oddzielna kopia z otwarty w Projektancie (Kopiuj dane wyjściowe są przechowywane w *\bin* katalogu dla programu Visual Basic i *\bin\debug* katalogu w języku C#).  
  
 Można włączyć ochrony na kopię dokumentu, który zostanie otwarty w Projektancie zamknięcie projektu programu Visual Studio, otwierając kopię dokumentu, który znajduje się w katalogu projektu i włączając ochronę.  
  
## <a name="enforce-word-document-protection-on-build"></a>Wymuszanie ochrony dokumentu programu Word w kompilacji  
 Visual Studio uruchamia Wymuszanie ochrony dokumentów programu Word i szablonów podczas procesu kompilacji jest włączona ochrona po otwarciu dokumentu do debugowania. Dokument jest chroniony za pomocą pustego hasła.  
  
 Ochrona jest włączona, podczas kompilacji tak że jeśli brak kodu w dokumencie <xref:Microsoft.Office.Tools.Word.Document.Startup> zdarzenia, które mogą spowodować wyjątków lub zmiany zachowania aplikacji, ten kod może być debugowany poprawnie. Po włączeniu ochrony po otwarciu dokumentu, kod inicjujący nie można debugować lub przetestowane.  
  
## <a name="setting-the-password"></a>Ustawianie hasła  
 Visual Studio automatycznie włącza ochronę, ale zapewnia bez hasła domyślnie. Jeśli chcesz ochrona dokumentu hasło, należy dodać przed wdrożeniem rozwiązania. Dodanie hasła umożliwia zezwala autoryzowanym użytkownikom usuwanie ochrony dokumentu. bez hasła nie można łatwo usunąć ochrony. Aby uzyskać więcej informacji o ustawianiu hasła Zobacz Pomoc w określonej aplikacji pakietu Office.  
  
## <a name="see-also"></a>Zobacz także  
 [Porady: programowane Włączanie ochrony dokumentów i części dokumentów](../vsto/how-to-programmatically-protect-documents-and-parts-of-documents.md)   
 [Office development ― przykłady i wskazówki](../vsto/office-development-samples-and-walkthroughs.md)   
 [Zarządzanie prawami do informacji i rozszerzenia kodu zarządzanego ― omówienie](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Ochrona za pomocą hasła w dokumentach pakietu Office](../vsto/password-protection-on-office-documents.md)   
 [Porady: zezwalanie kodu do uruchomienia w tle dokumentów z ograniczonymi uprawnieniami](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)  
  
  