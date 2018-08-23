---
title: Wyświetlanie plików za pomocą polecenia Otwórz plik | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project types, supporting Open File command
- Open File command
- persistence, supporting Open File command
ms.assetid: 4fff0576-b2f3-4f17-9769-930f926f273c
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 139eb83f2260c44a3e0f8c50868d42aca8160694
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42682298"
---
# <a name="displaying-files-by-using-the-open-file-command"></a>Wyświetlanie plików za pomocą polecenia Otwórz plik
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [wyświetlanie plików za pomocą polecenia Otwórz plik](https://docs.microsoft.com/visualstudio/extensibility/internals/displaying-files-by-using-the-open-file-command).  
  
W poniższych krokach opisano sposób obsługi IDE **Otwórz plik** polecenia, które jest dostępne w **pliku** menu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. W krokach opisano również, jak projekty powinny odpowiadać na wywołania, które pochodzą z tego polecenia.  
  
 Kiedy użytkownik kliknie **Otwórz plik** polecenie **pliku** menu i wybierze plik z **Otwórz plik** występuje następujący proces, okno dialogowe.  
  
1.  Za pomocą uruchomionej tabeli dokumentu, IDE ustala, czy plik jest już otwarty w projekcie.  
  
    -   Jeśli plik jest otwarty, IDE resurfaces okna.  
  
    -   Jeśli plik nie jest otwarty, IDE wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> kwerendy każdego projektu w celu określenia, który projekt można otworzyć pliku.  
  
        > [!NOTE]
        >  W danej implementacji projektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>, podaj wartość priorytetu, który wskazuje poziom, w którym projekt zostanie otwarty plik. Wartości priorytetu znajdują się w <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> wyliczenia.  
  
2.  Każdy projekt odpowiada za pomocą poziom priorytetu, która wskazuje ważność umieszcza się go z tego projektu, można otworzyć pliku.  
  
3.  IDE używa następujących kryteriów, aby ustalić, który projekt zostanie otwarty plik:  
  
    -   Projekt, który odpowiada o najwyższym priorytecie (DP_Intrinsic) otwiera plik. Jeśli więcej niż jeden projekt odpowiada za pomocą tego priorytetu, pierwszy projekt na otwiera plik.  
  
    -   Jeśli nie odpowiada projektu o najwyższym priorytecie (DP_Intrinsic), ale wszystkie odpowiada projektów z priorytetem tego samego, dolna, aktywny projekt, otwiera plik. Jeśli projekt nie jest aktywna, pierwszy projekt na otwiera plik.  
  
    -   Jeśli projekt nie oświadczeń własności pliku (DP_Unsupported), w projekcie plików pozostałych otwiera plik.  
  
         Jeśli jest tworzone wystąpienie projektu różne pliki projektu są zawsze odpowiada wartością DP_CanAddAsExternal. Ta wartość wskazuje, że projekt można otworzyć pliku. Ten projekt jest używany do przechowywania otwartych plików, które nie są w innym projekcie. Na liście elementów w tym projekcie, nie jest trwały; Ten projekt jest widoczna w **Eksploratora rozwiązań** tylko wtedy, gdy jest używany do otwarcia pliku.  
  
         Jeśli w projekcie plików pozostałych nie wskazuje, że plik można otworzyć, wystąpienie projektu nie utworzono. W tym przypadku IDE tworzy wystąpienie projektu różne pliki i informuje projekt można otworzyć pliku.  
  
4.  Jak najszybciej IDE ustala, który projekt zostanie otwarty plik wywoływanych przez nią <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> metody w tym projekcie.  
  
5.  Projekt następnie ma możliwość otwarcia pliku przy użyciu edytora specyficznych dla projektu lub edytora standardowego. Aby uzyskać więcej informacji, zobacz [porady: otwieranie edytorów specyficznych dla projektu](../../extensibility/how-to-open-project-specific-editors.md) i [porady: otwieranie standardowych edytorów](../../extensibility/how-to-open-standard-editors.md)odpowiednio.  
  
## <a name="see-also"></a>Zobacz też  
 [Wyświetlanie plików za pomocą polecenia Otwórz za pomocą polecenia](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)   
 [Otwieranie i zapisywanie elementów projektu](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Porady: otwieranie edytorów specyficznych dla projektu](../../extensibility/how-to-open-project-specific-editors.md)   
 [Instrukcje: otwieranie standardowych edytorów](../../extensibility/how-to-open-standard-editors.md)

