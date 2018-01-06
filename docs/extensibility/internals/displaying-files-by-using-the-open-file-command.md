---
title: "Wyświetlanie plików za pomocą polecenia Otwórz plik | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project types, supporting Open File command
- Open File command
- persistence, supporting Open File command
ms.assetid: 4fff0576-b2f3-4f17-9769-930f926f273c
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 75d714399f851aa479f398064e576790c793fffa
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="displaying-files-by-using-the-open-file-command"></a>Wyświetlanie plików za pomocą polecenia Otwórz plik
W poniższych krokach opisano sposób obsługi IDE **Otwórz plik** polecenia, który jest dostępny na **pliku** w menu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Również w krokach opisano, jak projekty powinny odpowiadać na wywołania, które pochodzą z tego polecenia.  
  
 Gdy użytkownik kliknie **Otwórz plik** na **pliku** menu i wybiera plik z **Otwórz plik** odbywa się następujący proces okno dialogowe.  
  
1.  Przy użyciu uruchomionej tabeli dokumentu, IDE Określa, czy plik jest już otwarty w projekcie.  
  
    -   Jeśli plik jest otwarty, IDE resurfaces okna.  
  
    -   Jeśli plik nie jest otwarty, wywołuje metodę IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> do każdego projektu, aby określić, który projekt można otworzyć pliku zapytania.  
  
        > [!NOTE]
        >  W implementacji projektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>, podaj wartość priorytetu, która wskazuje poziom, co powoduje otwarcie tego pliku projektu. Wartości priorytetu znajdują się w <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> wyliczenia.  
  
2.  Każdy projekt odpowie poziom priorytetu, która wskazuje znaczenie umieszcza z tego projektu, aby otworzyć plik.  
  
3.  IDE korzysta z następujących kryteriów, aby określić, który projekt zostanie otwarty plik:  
  
    -   Projekt, który odpowiada z najwyższym priorytetem (DP_Intrinsic) powoduje otwarcie tego pliku. Jeśli odpowiada więcej niż jednego projektu z tego priorytetu, pierwszy projekt odpowiada otwiera plik.  
  
    -   Jeśli nie odpowiada projektu z najwyższym priorytetem (DP_Intrinsic), ale wszystkie projekty odpowiedź z tej samej, niższy priorytet, aktywnego projektu otwiera plik. Jeśli nie ma aktywnych projektów, pierwszy projekt odpowiada otwiera plik.  
  
    -   Jeśli żaden projekt oświadczeń własność pliku (DP_Unsupported), w projekcie plików pozostałych otwiera plik.  
  
         Jeśli jest tworzone wystąpienie projektu różne pliki projektu zawsze odpowiada wartości DP_CanAddAsExternal. Ta wartość wskazuje, że projekt będzie mógł otworzyć plik. Ten projekt jest używany do przechowywania otwartych plików, które nie należą do innych projektów. Na liście elementów w tym projekcie nie jest trwały; Ten projekt jest widoczny w **Eksploratora rozwiązań** tylko, jeśli jest używany do otwarcia pliku.  
  
         Jeśli w projekcie plików pozostałych nie wskazuje, że plik można otworzyć, wystąpienie projektu nie został utworzony. W takim przypadku IDE tworzy wystąpienie projektu różne pliki i informuje projektu do otwierania pliku.  
  
4.  Jak IDE Określa, który projekt zostanie otwarty plik, wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> metody dla tego projektu.  
  
5.  Projekt posiada następnie możliwość otwierania pliku przy użyciu edytora określonego projektu lub standardowego edytora. Aby uzyskać więcej informacji, zobacz [porady: Otwórz edytory specyficznego dla projektu](../../extensibility/how-to-open-project-specific-editors.md) i [porady: Otwórz standardowe edytory](../../extensibility/how-to-open-standard-editors.md)odpowiednio.  
  
## <a name="see-also"></a>Zobacz też  
 [Wyświetlanie plików przy użyciu Otwórz za pomocą polecenia](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)   
 [Otwieranie i zapisywanie elementów projektu](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Porady: Otwórz edytory specyficznego dla projektu](../../extensibility/how-to-open-project-specific-editors.md)   
 [Instrukcje: otwieranie standardowych edytorów](../../extensibility/how-to-open-standard-editors.md)