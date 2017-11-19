---
title: "Zapytanie edycji zapytania Zapisz (VSPackage kontroli źródła) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- QEQS events
- Query Edit Query Save events
- source control packages, Query Edit Query Save events
ms.assetid: c360d2ad-fe42-4d65-899d-d1588cc8a322
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0aeb24f52b1b6b719e81dcd1a9bd93bd5822f8e6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="query-edit-query-save-source-control-vspackage"></a>Edytuj zapytania Zapisz (VSPackage kontroli źródła)
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]edytory może emitować zdarzenia zapytania Edytuj zapytania Zapisz (QEQS). [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Stub kontroli źródła implementuje usługę QEQS tak, aby odbiorcy zdarzeń QEQS. Zdarzenia te są następnie delegowane do kontroli źródła aktualnie aktywny pakiet VSPackage. Kontroli źródła active implementuje pakiet VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> i jego metod. Metody `IVsQueryEditQuerySave2` interfejsu są zwykle nazywane bezpośrednio przed dokumentu jest edytowany po raz pierwszy i bezpośrednio przed zapisaniu dokumentu.  
  
## <a name="queryeditquerysave-events"></a>Zdarzenia QueryEditQuerySave  
 Pakiet VSPackage kontroli źródła muszą obsługiwać zdarzenia QEQS zaimplementowanie `IVsQueryEditQuerySave2` interfejsu i niezbędne metody. Poniżej znajduje się krótki opis z dwóch metod, które pakiet VSPackage musi implementować co najmniej. Rzeczywista implementacja muszą być zgodne z logiką model kontroli źródła.  
  
### <a name="queryeditfiles-method"></a>QueryEditFiles — metoda  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> Jest wywoływane, gdy projekt lub Edytor chce modyfikacji pliku. Najlepiej, jeśli ta metoda jest wywoływana *przed* plik został zmodyfikowany, a jeśli plik jest zapisywany. Gdy została wywołana, `IVsQueryEditQuerySave2::QueryEditFiles` metoda sprawdza, czy pliki w danym są pod kontrolą źródła, czy muszą zostać wyewidencjonowany i czy można wykorzystać. Jeśli okoliczności uniemożliwiają pliki można ją edytować, `IVsQueryEditQuerySave2::QueryEditFiles` metody informuje program wywołujący, aby anulować edycję. Istnieje również możliwość dla obiekt wywołujący, aby określić tryb wywołania. W trybie "cichym" Ta metoda przyjmuje akcji tylko wtedy, gdy nie powoduje żadnych interfejsu użytkownika i pojawienie się. Interfejs użytkownika jest niezbędne, flagę musi zwracane do wskazują problem.  
  
 Metoda działa w sposób transakcyjnych; oznacza to czy edycja jest anulowane w pojedynczy plik, edycji zostało anulowane dla wszystkich plików. Z drugiej strony Jeśli edycja jest dozwolone, jest dozwolona dla wszystkich plików. Jeśli ta metoda umożliwia edytowanie raz dla danego zestawu plików, jego musi zawsze Zezwalaj na edycję na wezwań do tego samego zestawu plików. Pętla Zezwalaj edycji jest powtarzany do momentu zamknięty, zapisywania i ponownie załadować; pliki dopóki zmian ich atrybutów (właściwości); lub do momentu zmiany pakiet kontroli źródła. Przypadków wziąć pod uwagę w przypadku implementowania `IVsQueryEditQuerySave2::QueryEditFiles` metody obejmują wiele plików, pliki specjalne, Anuluj od użytkownika i edycję w pamięci.  
  
### <a name="querysavefiles-method"></a>QuerySaveFiles — metoda  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> Jest wywoływane, gdy projekt lub Edytor potrzebne do zapisania zestawu plików. Gdy została wywołana, `IVsQueryEditQuerySave2::QuerySaveFiles` metoda sprawdza, jeśli dany pliki są tylko do odczytu i czy są one pod kontrolą źródła. Jeśli pliki muszą być wyewidencjonowany, wywołanie jest delegowane do pakiet kontroli źródła. Jeśli okoliczności uniemożliwić pliki są zapisywane, `IVsQueryEditQuerySave2::QuerySaveFiles` metody należy wskazać anulować zapisywanie w edytorze. Jak `IVsQueryEditQuerySave2::QueryEditFiles` metody, jest możliwe w dla obiekt wywołujący, aby określić tryb wywołania. W trybie "cichym" Ta metoda przyjmuje akcji tylko wtedy, gdy nie powoduje żadnych interfejsu użytkownika i pojawienie się. Interfejs użytkownika jest niezbędne, flagę musi zwracane do wskazują problem.  
  
 Ta metoda musi się odbywać na sposób transakcyjnych; oznacza to jeśli zostało anulowane, Zapisz na pojedynczy plik, Zapisz zostało anulowane dla wszystkich plików. Z drugiej strony Jeśli zapisywania jest dozwolone, wymagane jest zezwolenie dla wszystkich plików. Jak `IVsQueryEditQuerySave2::QueryEditFiles` metody, należy wziąć pod uwagę w przypadku implementowania przypadków `IVsQueryEditQuerySave2::QuerySaveFiles` metody obejmują wiele plików, pliki specjalne, Anuluj od użytkownika i edycję w pamięci.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>