---
title: "Formant symbolu (VSPackage kontroli źródła) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- glyphs, source control packages
- source control packages, glyphs
ms.assetid: b9413b08-b3c3-4fc3-a6e0-3dc0db3652d7
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e41fc2a7d09f50d70caca939e3fdd691b1d05c9e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="glyph-control-source-control-vspackage"></a>Formant symbolu (VSPackage kontroli źródła)
Część głęboką integrację dostępne do VSPackages kontroli źródła jest możliwość wyświetlania własnych obiektów glyphs informującą o stanie elementów pod kontrolą źródła.  
  
## <a name="levels-of-glyph-control"></a>Poziomy kontroli symbolu  
 Stan symbolu jest ikonę, która wskazuje bieżący stan elementu podczas wyświetlania, na przykład w **Eksploratora rozwiązań** lub **widoku klasy**. Kontroli źródła pakiet VSPackage można wykonywać dwa poziomy kontroli symbolu. Można ograniczyć wybór symboli do wstępnie zdefiniowane symbole udostępnione przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE lub ją zdefiniować niestandardowy zestaw symboli do wyświetlenia.  
  
### <a name="default-set-of-glyphs"></a>Domyślny zestaw symboli  
 Aby ustalić symboli stanu, które są skojarzone z elementem w **Eksploratora rozwiązań**, projektu żądań symbolu stanu z używania kontroli źródła <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph%2A>. Kontroli źródła pakiet VSPackage może zdecydować zachować wybór symboli ograniczone do wstępnie zdefiniowane symbole udostępnione przez IDE. W takim przypadku pakiet VSPackage odsyła tablicy wartości reprezentujących wyliczenia symbolu, które są zdefiniowane w vsshell.idl. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon> . Jest to wstępnie zdefiniowane symbole ustawić IDE, takich jak kłódka dla symbolu "Zaewidencjonowania" i znacznik wyboru jako symbolu "Wyewidencjonowany".  
  
### <a name="custom-set-of-glyphs"></a>Niestandardowy zestaw symboli  
 Kontroli źródła pakiet VSPackage można używać własnej symboli unikatowy "wygląd i działanie" po jej zainstalowaniu. Gdy nowy pakiet VSPackage kontroli źródła jest aktywny, powinno być możliwe jej uruchomienie, przy użyciu własnego symboli, nawet jeśli pakiet VSPackage kontroli źródła poprzedniego jest nadal załadowany, ale nieaktywne. W tym trybie kontroli źródła pakiet VSPackage nadal można użyć istniejącego ikony aby zapewnić spójne z wyszukiwania [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Jeśli wybiera.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> Usługi obsługuje interfejs <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>, który opcjonalnie można wdrożyć pakiet VSPackage i który będzie wymagane podanie IDE. Gdy żądanie, sprawia, że IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] z kolei spróbuje uzyskać ten interfejs z kontroli źródła obecnie zarejestrowaną pakiet VSPackage. Jeśli istnieje interfejs w zarejestrowany pakiet VSPackage, żądania IDE dla niestandardowych symboli zakończy się pomyślnie; w przeciwnym razie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE używa swojego domyślnego zestawu symboli.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A> Metoda jest używana przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] stwierdza, aby uzyskać listę obrazów pokazywanie różnych kontroli źródła. Kontroli źródła pakiet VSPackage zwraca IDE dojścia do listy obrazów do jego niestandardowe symboli. IDE tworzy kopię listy obrazów w tym momencie i używa go później wybierz symboli do wyświetlenia. Jeśli nowy interfejs nie jest obsługiwana lub `IVsSccGlyphs::GetCustomGlyphList` metoda zwraca E_NOTIMPL, a następnie IDE pobiera jego symboli z listy domyślny symboli dostarczonych przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>