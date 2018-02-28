---
title: Kreatorzy | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], providing wizard support
ms.assetid: 59d9a77f-ee80-474b-a14f-90f477ab717b
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 96d91fa687c914f0c3f98c4ddca64a93a5d70d02
ms.sourcegitcommit: bd16e764134c436d2d2f46490f51234d5246ee50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/22/2018
---
# <a name="wizards"></a>Kreatorzy
Po utworzeniu kreatora zazwyczaj chcesz dodać go do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zintegrowane środowisko programistyczne (IDE), tak aby inne osoby go używać. Pojawi się w Kreatorze dodano **Dodawanie nowego projektu** lub **Dodaj nowy element** okien dialogowych. Aby wyświetlić **Dodawanie nowego projektu** lub **Dodaj nowy element** okno dialogowe pola, kliknij prawym przyciskiem myszy Otwórz rozwiązanie w **Eksploratora rozwiązań**, wskaż polecenie **Dodaj**, i następnie kliknij przycisk **nowy projekt** lub **nowy element**.  
  
 Kreatorzy mogą być implementowane w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] umożliwi użytkownikom wybierz jedną z dostępnych wartości po otwarciu w widoku drzewa **Dodawanie nowego projektu** okno dialogowe lub **Dodaj nowy element** okno dialogowe, lub jeśli ich kliknij prawym przyciskiem myszy element **Eksploratora rozwiązań**.  
  
 Zapewniają możliwość lokalizowanie nazwę nowego projektu lub ites kreatora, i ikony, którą użytkownicy zobaczą, gdy wybierają kreatora można określić. Można też kontrolować kolejność wyświetlania nowych elementów względem innych dostępnych elementów; elementy nie trzeba być alfabetycznej.  
  
 Może też podawać kreatora, który uruchamia inaczej, na podstawie niestandardowych parametrów, które są przekazywane do kreatora po otwarciu.  
  
 Tematy w tej sekcji omówiono w nim pliki, które implementuje spowodować [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Dodawanie nowego projektu** i **Dodaj nowy element** okien dialogowych, aby wyświetlić listę kreatora spośród dostępnych kreatorów i szablony, i wymagania, które kreatora muszą spełnić, aby działać poprawnie w środowisku IDE.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Opis katalogu szablonu (pliki Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)  
 Zawiera omówienie którego szablonu plików z katalogu opis wraz z wyjaśnieniem ich działania w środowisku IDE, aby wyświetlić folderów, plików kreatora .vsz i plików szablonów, które są skojarzone z projektem w oknach dialogowych.  
  
 [Kreator (plik Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)  
 Wyjaśnia sposób IDE uruchamiania kreatorów i zawiera trzy części pliku .vsz.  
  
 [Interfejs kreatora (IDTWizard)](../../extensibility/internals/wizard-interface-idtwizard.md)  
 W tym artykule opisano `IDTWizard` interfejs, który kreatorów musi implementować do pracy w środowisku IDE.  
  
 [Parametry kontekstu](../../extensibility/internals/context-parameters.md)  
 Wyjaśniono implementowania kreatorów i występujące podczas IDE przekazuje parametrów kontekstu do wykonania.  
  
 [Parametry niestandardowe](../../extensibility/internals/custom-parameters.md)  
 Wyjaśniono, jak używać parametrów niestandardowych do kontroli działania kreatora, po uruchomieniu kreatora.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Typy projektów](../../extensibility/internals/project-types.md)  
 Zawiera łącza do dodatkowych tematów, które oferują informacji dotyczących sposobu projektowania nowych typów projektów.  
  
 [Rozszerzanie projektów](../../extensibility/extending-projects.md)  
 Informacje dotyczące używania [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projekty i rozwiązania można organizować pliki kodu i plików zasobów i implementowania kontroli źródła.