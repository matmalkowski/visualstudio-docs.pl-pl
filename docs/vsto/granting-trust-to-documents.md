---
title: Udzielanie zaufania do dokumentów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], trust
- inclusion lists [Office development in Visual Studio], about inclusion lists
- trust [Office development in Visual Studio], 2007 Office system
- granting trust [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e8556f77b74ee1dab6a257f5ed3634da4bf798cd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="granting-trust-to-documents"></a>Udzielanie zaufania do dokumentów
  Projekt poziomie dokumentu ma te same wymagania zabezpieczeń jako projektów na poziomie aplikacji: podpisywanie manifestów przy użyciu certyfikatu lub klikając wiersz zaufania. Ponadto dokumentu lub skoroszytu musi znajdować się w katalogu, który jest oznaczony jako zaufanej lokalizacji.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="trusted-locations"></a>Zaufanych lokalizacji  
 Aplikacje w [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] i pakiet Office 2010 centrów zaufania, której użytkownicy mogą skonfigurować ustawienia zabezpieczeń i prywatności, takie jak zaufanych lokalizacji. Dla rozwiązań pakietu Office komputer lokalny jest traktowany jako zaufanej lokalizacji. Z powodu większe ryzyko, istnieją pewne katalogi, które nigdy nie może być zaufanych, takich jak foldery tymczasowe dla systemu, dla każdego użytkownika i programu Internet Explorer.  
  
 Aby uzyskać więcej informacji na temat Centrum zaufania, zobacz [i zasady ustawień zabezpieczeń i w pakiecie Office 2010](http://go.microsoft.com/fwlink/?LinkId=89202). Aby uzyskać więcej informacji dotyczących sposobu tworzenia, zarządzania, Usuń i Konfigurowanie zaufanych folderów, zobacz [skonfigurować zaufane lokalizacje i ustawienia zaufanych wydawców w pakiecie Office system 2007](http://go.microsoft.com/fwlink/?LinkId=89203) i [Utwórz, usuń lub zmień zaufanej lokalizacji plików](https://support.office.com/en-au/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).  
  
## <a name="security-considerations-for-office-solutions"></a>Zagadnienia dotyczące zabezpieczeń dla rozwiązań pakietu Office  
 Istnieje kilka bezpieczeństwem podczas należy wziąć pod uwagę foldery, które można dodać do zaufanych lokalizacji:  
  
-   Foldery lokalne są traktowane jako jedna jest bezpieczna i użytkownik ufa. Lokalizacjach zdalnych, takich jak udziały plików muszą być wyznaczone jako zaufane.  
  
-   Po dodaniu katalogu do zaufanej lokalizacji, ta akcja spowoduje przyznanie pełnego zaufania nie tylko do rozwiązań pakietu Office, ale do kodu VBA i ActiveX. Z tego powodu katalogu głównego i Moje dokumenty folderów nie powinno być wyznaczone jako zaufany.  
  
-   Chociaż samego dokumentu jest zaufany, korzystając z zaufanych lokalizacji, aby zaufać dostosowania są wymagane dodatkowe uprawnienia. Można przyznać pełne zaufanie dostosowań przy użyciu manifestów przy użyciu certyfikatu podpisywania, klikając wiersz zaufania lub instalowanie rozwiązania pakietu Office do katalogu zawierającego pliki programów.  
  
-   Dokument lub skoroszyt rozwiązanie na poziomie dokumentu można przechowywać w tym samym katalogu co zestaw lub w innym katalogu. Na przykład dokumentu może znajdować się na serwerze programu SharePoint i zestaw może znajdować się w sieciowym udziale plików. Aby uzyskać więcej informacji, zobacz [porady: publikowanie rozwiązań Office poziomie dokumentu na serwerze programu SharePoint za pomocą technologii ClickOnce za pomocą](http://msdn.microsoft.com/en-us/2408e809-fb78-42a1-9152-00afa1522e58).  
  
## <a name="see-also"></a>Zobacz też  
 [Udzielanie zaufania do rozwiązań pakietu Office](../vsto/granting-trust-to-office-solutions.md)   
 [Rozwiązywanie problemów z zabezpieczeniami rozwiązań pakietu Office](../vsto/troubleshooting-office-solution-security.md)   
 [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)  
  
  