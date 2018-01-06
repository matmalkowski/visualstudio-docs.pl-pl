---
title: 'Porady: Tworzenie niestandardowego tekstu znaczniki | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - custom text markers
ms.assetid: 6e32ed81-c604-4a32-9012-8db3bec7c846
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: d30ad5b61f59e6183067ddcc789b2fc796c7aef9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-custom-text-markers"></a>Porady: Tworzenie niestandardowego tekstu znaczników
Jeśli chcesz utworzyć znacznik niestandardowy tekst, aby wyróżnić lub organizowanie kodu, należy wykonać następujące czynności:  
  
-   Zarejestrować nowego znacznika tekstu, tak aby inne narzędzia do niego dostęp  
  
-   Domyślna implementacja i konfiguracji znacznika tekstu  
  
-   Utwórz usługę, która jest używana przez inne procesy, aby użyć znacznika tekstu  
  
 Aby uzyskać więcej informacji na temat sposobu zastosowania znacznika tekstu w regionie kod, zobacz [porady: Użyj znacznikach tekstu](../extensibility/how-to-use-text-markers.md).  
  
### <a name="to-register-a-custom-marker"></a>Aby zarejestrować znacznika niestandardowego  
  
1.  Utwórz wpis rejestru w następujący sposób:  
  
     HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<wersji >*znaczniki \Text Editor\External\\*\<MarkerGUID >*  
  
     *\<MarkerGUID >*jest `GUID` używany do identyfikowania znaczników dodaniu  
  
     *\<Wersja >* jest wersja [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], na przykład 8.0  
  
     *\<PackageGUID >* jest identyfikatorem GUID VSPackage implementacja obiektu automatyzacji.  
  
    > [!NOTE]
    >  Ścieżka katalogu głównego HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<wersji >* może zostać zastąpiona przez alternatywny głównego po zainicjowaniu powłoki programu Visual Studio, aby uzyskać więcej informacji, zobacz [Przełączniki wiersza polecenia](../extensibility/command-line-switches-visual-studio-sdk.md).  
  
2.  Utwórz cztery wartości w obszarze HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<wersji >*\Text Editor\External znaczniki\\*\<MarkerGUID >*  
  
    -   (Domyślnie)  
  
    -   Usługa  
  
    -   Nazwa wyświetlana  
  
    -   Package  
  
    -   `Default`wpis jest opcjonalny typu REG_SZ. Po ustawieniu wartości wpisu jest ciąg zawierający niektóre przydatne informacje identyfikacyjne, na przykład "niestandardowego tekstu znacznika".  
  
    -   `Service`jest wpisu typu REG_SZ zawierające ciąg identyfikatora GUID usługi, która zawiera znacznik niestandardowy tekst przez proffering <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>. Format to {XXXXXX XXXX XXXX XXXX XXXXXXXXX}.  
  
    -   `DisplayName`to wpisu typu REG_SZ zawierający identyfikator zasobu Nazwa znacznika tekstu niestandardowego. Format jest #YYYY.  
  
    -   `Package`wpis typu REG_SZ zawierających `GUID` pakiet VSPackage, która dostarcza usługę wymienionych w ramach usługi. Format to {XXXXXX XXXX XXXX XXXX XXXXXXXXX}.  
  
### <a name="to-create-a-custom-text-marker"></a>Aby utworzyć znacznik niestandardowy tekst  
  
1.  Implementowanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType> interfejsu.  
  
     Implementacji ten interfejs definiuje zachowania i wyglądu tego typu znacznika niestandardowego.  
  
     Ten interfejs jest wywoływane, gdy  
  
    1.  Użytkownik uruchamia IDE po raz pierwszy.  
  
    2.  Inny użytkownik wybierze **Resetuj** przycisku w obszarze **czcionki i kolory** stronę właściwości w **środowiska** folderu, znajdującego się w lewym okienku  **Opcje** okno dialogowe uzyskane z **narzędzia** menu IDE.  
  
2.  Implementowanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider.GetTextMarkerType%2A> metody, która wskazujące `IVsPackageDefinedTextMarkerType` implementacji powinny być zwróconych na podstawie typ znacznika GUID określonych w wywołaniu metody.  
  
     Środowisko wywołuje metody pierwszy teraz danego typu znacznik niestandardowy jest tworzony i określa identyfikator GUID typu znacznika niestandardowego.  
  
### <a name="to-proffer-your-marker-type-as-a-service"></a>Aby proffer danego typu znacznika jako usługa  
  
1.  Wywołanie <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponentManager.QueryService%2A> metodę <xref:Microsoft.VisualStudio.Shell.Interop.SProfferService>.  
  
     Wskaźnik do <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> jest zwracany.  
  
2.  Wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.ProfferService%2A> metody, określając identyfikator GUID identyfikowanie znacznika niestandardowego typu usługi i zapewnianie wskaźnik do implementacji <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> interfejsu. Twoje <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> implementacji powinien zwraca wskaźnik do implementacji <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider> interfejsu.  
  
     Plik cookie unikatowy identyfikujący, zwracany jest usługą. Ten plik cookie mógł później użyć, aby odwołać usługą znacznika niestandardowego typu przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> metody <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> interfejsu określenie tej wartości pliku cookie.  
  
## <a name="see-also"></a>Zobacz też  
 [Przy użyciu znaczników tekstu przy użyciu interfejsu API starsza wersja](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Porady: Dodawanie znaczników tekstu standardowego](../extensibility/how-to-add-standard-text-markers.md)   
 [Porady: Implementowanie znaczników błąd](../extensibility/how-to-implement-error-markers.md)   
 [Porady: Użyj znacznikach tekstu](../extensibility/how-to-use-text-markers.md)